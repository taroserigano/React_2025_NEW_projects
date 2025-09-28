# Create New Idea Form

We need to create the form to create the new idea. Then we will add the mutation and make the request to the API. The form will have the following fields:

- title
- excerpt
- description
- tags

We will also add a submit button to create the idea.

Open the `src/routes/ideas/new.tsx` file and add the following imports:

```tsx
import { createFileRoute, useNavigate } from '@tanstack/react-router';
import { useState } from 'react';
import { useMutation } from '@tanstack/react-query';
import type { Idea } from '@/types';
```

We will initialize the navigate function and the state for the new idea:

```tsx
function NewIdeaPage() {
  const navigate = useNavigate();
  const [title, setTitle] = useState('');
  const [summary, setSummary] = useState('');
  const [description, setDescription] = useState('');
  const [tags, setTags] = useState('');
  //...
}
```

Add the form and markup in the return:

```tsx
return (
  <div className='space-y-6'>
    <h1 className='text-3xl font-bold mb-6'>Create a New Idea</h1>

    <form className='space-y-4'>
      <div>
        <label htmlFor='title' className='block text-gray-700 font-medium mb-1'>
          Title
        </label>
        <input
          id='title'
          type='text'
          value={title}
          onChange={(e) => setTitle(e.target.value)}
          className='w-full border border-gray-300 rounded-md p-2 focus:outline-none focus:ring-2 focus:ring-blue-500'
          placeholder='Enter idea title'
        />
      </div>

      <div>
        <label
          htmlFor='summary'
          className='block text-gray-700 font-medium mb-1'
        >
          Summary
        </label>
        <input
          id='summary'
          type='text'
          value={summary}
          onChange={(e) => setSummary(e.target.value)}
          className='w-full border border-gray-300 rounded-md p-2 focus:outline-none focus:ring-2 focus:ring-blue-500'
          placeholder='Enter idea summary'
        />
      </div>

      <div>
        <label htmlFor='body' className='block text-gray-700 font-medium mb-1'>
          Description
        </label>
        <textarea
          id='body'
          value={description}
          onChange={(e) => setDescription(e.target.value)}
          rows={6}
          className='w-full border border-gray-300 rounded-md p-2 focus:outline-none focus:ring-2 focus:ring-blue-500'
          placeholder='Write out the description of your idea'
        />
      </div>

      <div>
        <label htmlFor='tags' className='block text-gray-700 font-medium mb-1'>
          Tags
        </label>
        <input
          id='tags'
          type='text'
          value={tags}
          onChange={(e) => setTags(e.target.value)}
          className='w-full border border-gray-300 rounded-md p-2 focus:outline-none focus:ring-2 focus:ring-blue-500'
          placeholder='optional tags, comma separated'
        />
      </div>

      <div className='mt-5'>
          <button
            type='submit'
            className='block w-full bg-blue-600 hover:bg-blue-700 text-white font-semibold px-6 py-2 rounded-md transition disabled:opacity-50 disabled:cursor-not-allowed'
          >
            Create Idea
          </button>
        </div>
    </form>
  </div>
);
```

Now that we have the form showing, we will work on creating the mutation and making the request in the next lesson.

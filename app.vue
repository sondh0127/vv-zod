<script lang="ts" setup>
import { z } from 'zod'
import { toTypedSchema } from '@vee-validate/zod'


const schema = z.object({
  id: z.string()
}).superRefine(() => {})

const { handleSubmit, meta, values, errors, resetForm } = useForm({
  initialValues: {
    id: ''
  },
  validationSchema: toTypedSchema(schema),
  keepValuesOnUnmount: true,
})
</script>

<template>
  <div>
    <Field name="id" v-slot="{ meta }">
      <details open>
        <summary>meta.required</summary>
        <pre>{{ JSON.stringify(meta.required, null, 2) }}</pre>
      </details>
    </Field>
  </div>
</template>

## @chakra-v2/querybuilder

Unofficial [react-querybuilder](https://npmjs.com/package/react-querybuilder) components for [Chakra UI v2 fork](https://github.com/userlike/chakra-v2).

## Installation

```bash
npm i react-querybuilder @chakra-v2/querybuilder @chakra-v2/icons @chakra-v2/react @emotion/react @emotion/styled framer-motion
# OR yarn add / pnpm add / bun add
```

## Usage

To render Chakra-compatible components in the query builder, wrap the `<QueryBuilder />` element in `<QueryBuilderChakra />`.

```tsx
import { QueryBuilderChakra } from '@chakra-v2/querybuilder';
import { ChakraProvider, extendTheme } from '@chakra-v2/react';
import { QueryBuilder, RuleGroupType } from 'react-querybuilder';

const chakraTheme = extendTheme();

const fields = [
  { name: 'firstName', label: 'First Name' },
  { name: 'lastName', label: 'Last Name' },
];

const App = () => {
  const [query, setQuery] = useState<RuleGroupType>({ combinator: 'and', rules: [] });

  return (
    <ChakraProvider theme={chakraTheme}>
      <QueryBuilderChakra>
        <QueryBuilder fields={fields} query={query} onQueryChange={q => setQuery(q)} />
      </QueryBuilderChakra>
    </ChakraProvider>
  );
};
```

## Notes

- Some additional styling may be necessary, e.g.:

  ```css
  .queryBuilder .chakra-select__wrapper {
    width: fit-content;
    display: inline-block;
  }

  .queryBuilder .chakra-input {
    width: auto;
    display: inline-block;
  }

  .queryBuilder .chakra-radio-group {
    display: inline-block;
  }
  ```

- This package exports `chakraControlElements` which can be assigned directly to the `controlElements` prop on `<QueryBuilder />` (and also exports each component individually), but this method does not support customized Chakra themes like `<QueryBuilderChakra />`.

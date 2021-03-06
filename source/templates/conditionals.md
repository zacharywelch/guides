Sometimes you may only want to display part of your template if a property
exists.

We can use the `{{#if}}` helper to conditionally render a block:

```handlebars
{{#if person}}
  Welcome back, <b>{{person.firstName}} {{person.lastName}}</b>!
{{/if}}
```

Handlebars will not render the block if the argument passed evaluates to
`false`, `undefined`, `null` or `[]` (i.e., any "falsy" value or an empty array).

If the expression evaluates to falsy, we can also display an alternate template
using `{{else}}`:

```handlebars
{{#if person}}
  Welcome back, <b>{{person.firstName}} {{person.lastName}}</b>!
{{else}}
  Please log in.
{{/if}}
```

Handlebars also supports chained else helpers, the most common use being else if. An example:

```handlebars
{{#if isAtWork}}
  Ship that code!
{{else if isReading}}
  You can finish War and Peace eventually...
{{/if}}
```

To only render a block if a value is falsy, use `{{#unless}}`:

```handlebars
{{#unless hasPaid}}
  You owe: ${{total}}
{{/unless}}
```

`{{#if}}` and `{{#unless}}` are examples of block expressions. These allow you
to invoke a helper with a portion of your template. Block expressions look like
normal expressions except that they contain a hash (#) before the helper name,
and require a closing expression.

You can also use the inline `{{if}}` helper:

```handlebars
<span class={{if isEnabled "enabled" "disabled"}}>Warning!</span>
```

In this case, if the `isEnabled` property is `true`, the `enabled` class will be
added. The second argument is optional and only necessary if you want to handle
the `false` case. Here, if the property is `false`, the class `disabled` will be
added.

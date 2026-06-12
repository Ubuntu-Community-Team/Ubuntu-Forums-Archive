---
title: "shell variable declaration"
date: 2010-03-06
forum: Desktop Environments
---

### Post by vksingh on 2010-03-06
Hi,

What is the difference between the following shell assignments:

$x="vivek"

$x=vivek

Please help.

Thanks,

Vivek

---

### Post by asmoore82 on 2010-03-06
For BASH, you don't use the dollar sign($) when declaring variables, only when referencing them.

It's good practice to always enclose the variable value in quotation marks
and always enclose variable references in quotation marks...

```
[COLOR="Red"]#sloppy work, no quotes[/COLOR]
**$** greeting=hello
**$** echo $greeting
hello
[COLOR="Red"]#will lead to errors[/COLOR]
**$** greeting=Hello World
[COLOR="Red"]World: command not found[/COLOR]

[COLOR="Blue"]#much better scripting[/COLOR]
**$** greeting="Hello World"
**$** echo "$greeting"
Hello World

[COLOR="Blue"]#declaring an array[/COLOR]
**$** conversation=( "$greeting" "How are you?" "Goodnight, ladies." )

[COLOR="Red"]#more sloppy work, no quotes leads to bad behavior[/COLOR]
**$** for message in ${conversation[@]}
**>** do
**>** echo $message
**>** done
Hello
World
How
are
you?
Goodnight,
ladies.

[COLOR="Blue"]#much better scripting[/COLOR]
**$** for message in "${conversation[@]}"
**>** do
**>** echo "$message"
**>** done
Hello World
How are you?
Goodnight, ladies.
```

---


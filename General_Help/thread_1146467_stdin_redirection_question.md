---
title: "stdin redirection question"
date: 2009-05-02
forum: General Help
---

### Post by Bas1234567 on 2009-05-02
Hello,

This is a problem I have with php, but I think some error with the linux command is the cause.

I'm trying to generate a dot image. Dot reads from standard in, and I have to complete the command in one line (since I'm running the command from within php)

I tried:

echo "digraph { a -> b; }" | dot -Tpng"

on the commandline and that seems to work.

But when I call it in PHP:

shell_exec("echo \"digraph { a -> b; }\" | dot -Tpng");

it doesn't do anything.

My php code doesn't seem to be the problem, since

shell_exec("ls");

correctly outputs the folder content.

Can somebody see what's going wrong here?

Regards,

Bas

---

### Post by Alterax on 2009-05-02
Ok, I've got it.  I think it's reading the binary data to stderr rather than stdout, which we'd expect. I altered this slightly by making the return of the command the value of a new variable called "$output" (can be anything for a name) and then echoed the result.

Here ya go!

```
  $output = shell_exec("echo 'digraph { a -> b; }' | dot -Tpng");
  echo $output;

```
> **Bas1234567 said:**
> Hello,

This is a problem I have with php, but I think some error with the linux command is the cause.

I'm trying to generate a dot image. Dot reads from standard in, and I have to complete the command in one line (since I'm running the command from within php)

I tried:

echo "digraph { a -> b; }" | dot -Tpng"

on the commandline and that seems to work.

But when I call it in PHP:

shell_exec("echo \"digraph { a -> b; }\" | dot -Tpng");

it doesn't do anything.

My php code doesn't seem to be the problem, since

shell_exec("ls");

correctly outputs the folder content.

Can somebody see what's going wrong here?

Regards,

Bas

---

### Post by Bas1234567 on 2009-05-02
Thanks for you answer!

I forgot to post that I was already doing that, I omitted it, to make it shorter, sorry. My complete code is:

```
<?php
$output = shell_exec("echo 'digraph { a -> b; }' | dot -Tpng");
header( "Content-type: image/png" ); 
echo $output;
?>
```

On the comandline it works, in the script it doesn't..

---


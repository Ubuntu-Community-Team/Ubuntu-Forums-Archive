---
title: "PHP5 functions returning syntax errors"
date: 2008-03-06
forum: Desktop Environments
---

### Post by archer007 on 2008-03-06
I have a 7.10 box running Apache2 and PHP5, and the Apache php module. However, no php functions will work except the "echo" command, which displays Strings perfectly.

The php file I used:

[PHP]
<?php
echo "Hai"

phpinfo();

?>
[/PHP]

Gives the following error:

```
Parse error: syntax error, unexpected T_STRING, expecting ',' or ';' in /var/www/test.php on line 4
```

I rebooted and re-installed PHP5 and the Apache php module using Synaptic. Can anyone tell me what is wrong?

---

### Post by jordanmthomas on 2008-03-07
You might get better help in another subforum.

---

### Post by mcduck on 2008-03-07
> **archer007 said:**
> I have a 7.10 box running Apache2 and PHP5, and the Apache php module. However, no php functions will work except the "echo" command, which displays Strings perfectly.

The php file I used:

[PHP]
<?php
echo "Hai"

phpinfo();

?>
[/PHP]

Gives the following error:

```
Parse error: syntax error, unexpected T_STRING, expecting ',' or ';' in /var/www/test.php on line 4
```

I rebooted and re-installed PHP5 and the Apache php module using Synaptic. Can anyone tell me what is wrong?
Your code is missing a semicolon on the "echo"-line. That's what the error message is trying to tell you.

[PHP]
<?php
echo "Hai";

phpinfo();

?>
[/PHP]

---

### Post by archer007 on 2008-03-07
Wow, I feel really stupid about that now. Thanks for your help, that was probably the problem.

---


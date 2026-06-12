---
title: "Bad substitution"
date: 2009-06-18
forum: General Help
---

### Post by jasch on 2009-06-18
Hopefully this is the right forums for this...

I am having trouble with a really simple shell script.

This WORKED on Ubuntu 6:

```
#!/bin/sh

echo "mail = $1"
echo "domn = ${1/*@/}"
```

If you ran it like this:

./script [email]email@domain.com[/email]

It produced this result:

[HTML]mail = email@domain.com
domn = domain.com[/HTML]

I upgraded to Ubuntu 9 this week, and the RegEx stopped working altogether.

[HTML]mail =email@domain.com
./script: 4: Bad substitution[/HTML]

I tried the script on my workstation (OS X) and it worked fine. 

What could be the problem?

Thanks in advance.

---

### Post by geirha on 2009-06-18
In Ubuntu 6.06, /bin/sh was a symlink to bash, which allows that syntax (${1/*@/}). In Ubuntu 6.10 and later, /bin/sh is a symlink to dash, which is a lighter shell that does not understand that syntax. Either change it to ${1#*@}, or change the hash-bang from #!/bin/sh to #!/bin/bash

See this page for a more thorough explanation: [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by jasch on 2009-06-18
Thank you. That was quick and perfect. I changed it to bash, so the rest of the script (ommited) remains 100% compatible as before.

---


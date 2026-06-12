---
title: "bash redirect stderr in script"
date: 2009-02-08
forum: General Help
---

### Post by starfry on 2009-02-08
Hi, hopefully an easy one but my mind is drawing a blank.

I know I can redirect stderr on the command line:

$ ./bash_script 2>&1

However, is there a way to do this inside bash_script so that it does not need to be given on the command line ?

I would want the stderr output of all commands invoked by the script to be redirected to stdout.

Thanks!

---

### Post by lha on 2009-02-08
> **starfry said:**
> Hi, hopefully an easy one but my mind is drawing a blank.

I know I can redirect stderr on the command line:

$ ./bash_script 2>&1

However, is there a way to do this inside bash_script so that it does not need to be given on the command line ?

I would want the stderr output of all commands invoked by the script to be redirected to stdout.

Thanks!

```

exec 2> out.txt

```

---


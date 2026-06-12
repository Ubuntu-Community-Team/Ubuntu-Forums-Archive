---
title: "Opening files with a custom shell script in Nautilus"
date: 2009-01-09
forum: Desktop Environments
---

### Post by Bachi76 on 2009-01-09
I'm trying to have JPGs opened in IrfanView via Wine by default. This requires a command like this:

```
wine "c:\Programme\Irfanview\i_view32.exe" d:\\Desktop\\Downloads\\portrait.jpg
```

Since it requires a pseudo windows path, I want to create a .sh script that issues this command based on the file path to be opened.

This is my first try with a bit of shell scripting. When I run this test script from the shell, I get the params as expected. 

However - when I tell Nautilus to open the .jpg file with this .sh file, I don't get any params, in fact it seems the script is not even called at all.

```
#!/bin/sh
echo Arguments: $# >> shltest.log
echo 0: $0 >> shtest.log
echo 1: $1 >> shtest.log
echo 2: $2 >> shtest.log
echo f: $f >> shtest.log
echo s: $s >> shtest.log
```

So, my newbie question - why does Nautilus apparently not run my .sh script when I tell it to open a file with a custom command ('/home/bachi/Desktop/shtest.sh' in my case)?

Thanks - Bachi

---

### Post by adamlau on 2009-01-09
chmod +x shell.script.sh

---

### Post by Bachi76 on 2009-01-11
It does have execute rights (as I wrote, it can be executed from the shell - not with Nautilus' "open with".

---


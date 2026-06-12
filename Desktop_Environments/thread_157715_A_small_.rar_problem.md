---
title: "A small .rar problem"
date: 2006-04-09
forum: Desktop Environments
---

### Post by Ob1 on 2006-04-09
I get this error msg

```
Encrypted file:  CRC failed in /home/johnny/000419.rar (password incorrect ?)
```

I have the password for the file, and I'm using Archive Manager, but my question is were do i enter the password?

---

### Post by Ob1 on 2006-04-09
damn, wrong sub-forum

---

### Post by ice60 on 2006-04-09
hi, are you using the rar program from [here](http://www.rarlab.com/)? if so i think all you have to do is this if the RAR's on your Desktop -

open a command line window and type this

```

cd Desktop
rar e **filename**
```

then it will say 
```
RAR 3.51   Copyright (c) 1993-2005 Alexander Roshal   7 Oct 2005
Shareware version         Type RAR -? for help


Extracting from Your_File.rar

Enter password (will not be echoed) for **[color=blue]this will be the name of the contents of your RAR[/color]**: **ENTER PASSWORD HERE** 
```
[color=red]Note[/color] you won't see the password as you type, so to make sure you get it correct paste it in using the Shift+Insert key combo

when you have put in the correct password you will then see this

```
Extracting  **Name of the contents of the RAR**  OK
All OK

```
that should be it you will have the extracted RAR on your Desktop :) HTHs

---


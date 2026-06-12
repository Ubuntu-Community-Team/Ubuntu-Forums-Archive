---
title: "OpenOffice - opening and saving"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Gryphin on 2006-09-12
Hello!
Whenever I try to open a new document or save one in openoffice the program just exits. I tried to lunch it in terminal and see what is going on and it actually does lunch there but it looks like this:

```
duncan@cameel:~$ ooffice
duncan@cameel:~$ 
```

and no other information is shown.

I use OO 2.0.3

---

### Post by Viskovitz on 2006-09-12
Well, I don't know what the problem is, but you can try launching it as:

```
ooffice -v
```
or
```
oowriter -v
```

and that will probably give you more information about what's going wrong.

---

### Post by Gryphin on 2006-09-12
Not much changed. Even if I use commands given above the cursor just moves to next line as if no program was lunched. The effect is similar to pressing enter without actually typing any command.

---

### Post by canadianwriterman on 2006-09-12
Did you upgrade to OpenOffice 2.0.3? I use the default install of OpenOffice with no problem. However, I notice that the crashing problem is on the experimental Edgy version, which uses 2.0.3.

---

### Post by Gryphin on 2006-09-13
In fact I did. :(

---

### Post by NoWhereMan on 2006-09-14
could you post here, once this have been fixed? I want to upgrade but I don't want to waste bandwith to download a broken iso ;)

thanks!
bye

---

### Post by Gryphin on 2006-09-14
I found out that only "open" and "save as..." commads cause OO to crash. Regular save (ctrl+s) and opening document by doubleclicking on it work fine.

---

### Post by NoWhereMan on 2006-09-15
> **Gryphin said:**
> I found out that only "open" and "save as..." commads cause OO to crash. Regular save (ctrl+s) and opening document by doubleclicking on it work fine.

ok. in fact they told me it's abi broken for the gtk open/save dialog. it will be probably fixed on the next update. if you posted here once this has been fixed that would be sooo kind :)

---

### Post by vrunner on 2006-09-18
Damn any solution this yet ? I'm in dire need of converting an odp file that I made to a ppt format !

[Edit: Nevermind, found a solution for now : [http://ubuntuforums.org/showpost.php?p=1477158&postcount=5](http://ubuntuforums.org/showpost.php?p=1477158&postcount=5) ]

---


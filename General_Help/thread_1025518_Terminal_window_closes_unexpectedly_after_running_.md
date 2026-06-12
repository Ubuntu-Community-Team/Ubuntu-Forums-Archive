---
title: "Terminal window closes unexpectedly after running script"
date: 2008-12-30
forum: General Help
---

### Post by sonik88 on 2008-12-30
Hello,

I have this weird problem, when I run a script the terminal window closes and doesn't print the results. The scripts are very small and straightforward.

An example:

#! /bin/bash
echo 'Please enter a directory'
read directory
echo 'Please enter a filename'
read filename
cd $directory
ls $filename -lg

In this one, the terminal window closes after reading the filename without printing anything.

I run Ubuntu 8.10 amd64 wubi installation but the same happened with 8.04 on the same system whether it is normal installation or wubi.

Thanks

---

### Post by Seks on 2008-12-30
Perhaps because it is finished? Have you tried opening an empty terminal first and then navigating to and running the script? (so instead of closing you would get another prompt)

---

### Post by sonik88 on 2008-12-30
:oops:

Thanks thats it...

But is there any command to "freeze" the shell before it closes?

---

### Post by caljohnsmith on 2008-12-30
> **sonik88 said:**
> :oops:

Thanks thats it...

But is there any command to "freeze" the shell before it closes?
How about trying:
```
gnome-terminal -x bash -c "[COLOR="Blue"]/path_to_myscript/My_script.sh[/COLOR];read -n1"
```
Replace "/path_to_myscript/My_script.sh" with your script, and then when you run the above command, it will pop open a terminal window, run the script, and then wait until you hit any key to close the Window. Let me know if that is what you are looking for. That's a generic way of doing it, but in your specific case you could simply add "read -n1" at the end of your script to accomplish the same thing I think.

---

### Post by sonik88 on 2008-12-31
Yep thats it...Thanks

---


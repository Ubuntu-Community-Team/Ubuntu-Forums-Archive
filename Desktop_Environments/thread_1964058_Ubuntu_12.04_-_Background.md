---
title: "Ubuntu 12.04 - Background"
date: 2012-04-23
forum: Desktop Environments
---

### Post by granul on 2012-04-23
Hi!

I'm trying to copy some image into usr/share/backgrounds, but I get an error message, access denied, and I cannot loggin as root under Ubuntu 12.04

How can I set permission to modify this folder.

Thank you

---

### Post by Novus Anima on 2012-04-23
Hi granul,

I had the same problem yesterday while I was trying to install Java manually onto my machine since the Software Center wasn't cooperating properly. There was a step in the guide that prompted me to put a file in the ~usr/lib/jvm folder, but I lacked permissions. Save the image to your Pictures or Downloads directory, then there is a command that *should* work the same as it would if you were to click and drag it into the folder. Let me know how it goes!

```
sudo cp your/file/directory /usr/share/backgrounds
```

---

### Post by granul on 2012-04-23
Thank you

So if I want to copy all the images I do : sudo cp Images/background /usr/share/backgrounds

---

### Post by Novus Anima on 2012-04-23
> **granul said:**
> Thank you

So if I want to copy all the images I do : sudo cp Images/background /usr/share/backgrounds

Yeah, that's all you would do. For example, I was trying to move a Java 7 config file from my Home folder and I input: "**sudo cp /home/matthew/java-7-config.jinfo /usr/lib/jvm**". The space is crucial, by the way, for you need to differentiate the directory you want the file in (right after 'sudo cp') and the file you wish to copy. You might have to chmod the file you're moving though. As of right now I don't remember the chmod syntax, so you'll have to forgive me.

EDIT: In theory I guess that would just copy the Pictures library to your usr/share/backgrounds directory. So, move the pictures manually. You might be able to separate multiple files with a comma; not 100% sure though. I'm rather new to Ubuntu, myself, but I do know some basic Terminal syntax.

---

### Post by granul on 2012-04-23
Thank you it work but I had to copy 1 image at the time, I cannot copy the whole folder

---

### Post by lisati on 2012-04-23
> **granul said:**
> Thank you it work but I had to copy 1 image at the time, I cannot copy the whole folder

If the folder you are copying from contains only image files that you want to copy, you can do this:
```
sudo cp [COLOR="Red"]-r[/COLOR] your/file/directory /usr/share/backgrounds
```
What the "-r" does is to ask the cp command to recursively copy the folder.

---


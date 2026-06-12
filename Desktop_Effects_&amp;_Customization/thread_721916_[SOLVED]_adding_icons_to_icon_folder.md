---
title: "[SOLVED] adding icons to icon folder"
date: 2008-03-11
forum: Desktop Effects &amp; Customization
---

### Post by DXM31 on 2008-03-11
I have a folder on my desktop with icons I got off the net
But I don't know how to get them to the icons folder
To be more specific I want to add mouse pointers but I don't now how
Whenever I try to move them to the folder I get an error cause I don't have permission to write to that folder.

---

### Post by insineratehymn on 2008-03-11
Ok, it seems like someone already asked launchpad this:

[https://answers.launchpad.net/ubuntu/+question/13446](https://answers.launchpad.net/ubuntu/+question/13446)

Looks like your answer lies in this:

Install gcursor:

sudo apt-get install gcursor

Then go to:

System->Preferences->Cursor Selection

That applet will allow you to select your desired mouse-pointer-file-things.

Have a nice day. :)

Edit:

Oh, about your permissions problem...

Short story:

Right-click on the folder and go to the "Permissions" tab.
You will see it broken into three settings; "User", "Group", "World"
Allow them whatever you want based on the properties of "Read", "write", and "execute".

Long story:

*ux uses an octal-based system for deciding permissions with the lowest level being 000 and the highest level being 777.
It is divided into the same "ugo" setup and is modified with the chmod command.
So, chmod 777 testFile would allow everyone read, write, and execute permissions on testFile.

---

### Post by DXM31 on 2008-03-11
Sweet, Thanks

---

### Post by DXM31 on 2008-03-11
I went to cursor selection and it was just the 5 or 6 that was there before
so
I went thru places and right clicked on the icons folder hit properties hit permissions and it said I am not the owner so I can't change permissions:confused:

---

### Post by insineratehymn on 2008-03-12
> Oh, about your permissions problem...

Short story:

Right-click on the folder and go to the "Permissions" tab.
You will see it broken into three settings; "User", "Group", "World"
Allow them whatever you want based on the properties of "Read", "write", and "execute".

Long story:

*ux uses an octal-based system for deciding permissions with the lowest level being 000 and the highest level being 777.
It is divided into the same "ugo" setup and is modified with the chmod command.
So, chmod 777 testFile would allow everyone read, write, and execute permissions on testFile.

Did you try that?

---

### Post by DXM31 on 2008-03-12
> **insineratehymn said:**
> Did you try that?

The short story one yes, that's when I discovered I don't own this computer

The long story, no, I only speak english I have no idea what that one is talking about.

---

### Post by rune0077 on 2008-03-12
Try like this: alt+F2. Then, in the box that pops up, enter this command:

```
gksu nautilus
```

Enter your password when prompted, and Nautilus should open with root access. You should now be able to copy-paste-whatever everywhere you want to.

---

### Post by DXM31 on 2008-03-12
That worked great I now own my computer again.
Added file now off to see what happens.
Thanks

---

### Post by rune0077 on 2008-03-12
> **DXM31 said:**
> That worked great I now own my computer again.
Added file now off to see what happens.
Thanks

Great. Just be careful with this, and don't use root access unless you need to. While you are browsing in "root-mode", you should also be able to change the file permissions, so if there's something you need to use regularly and you don't have permission to it, then change the permission so that in the future you can access those files without doing the root-thing first. Well, just a word of advice.

---

### Post by DXM31 on 2008-03-12
I only changed permissions on the Icons folder but I could certainly see where you could mess up a lot of stuff with this
By the way I got a new mouse cursor.

---


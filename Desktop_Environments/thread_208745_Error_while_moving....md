---
title: "Error while moving..."
date: 2006-07-04
forum: Desktop Environments
---

### Post by Miki01 on 2006-07-04
Okay, I've just went through the installation of 32-bit Firefox with Java and Flash from the tutorial [here]("https://help.ubuntu.com/community/FirefoxAMD64FlashJava"). When I finished, I deleted the folders I had used on my Desktop. There is one folder that won't delete though. Its entitled "jre1.5.0_07" I used it during the installation of Java. When I try to delete it I get an "Error while moving" error window saying:

>  Cannot move "/home/miki...re1.5.0_07" to the trash because you do not have permissions to change it or its parent

How did I lose permission to change this folder? How do I delete it? And whats this thing about "change it or its parent"? Will there be a side effect if I delete it?

Right-click>Properties>Permission leads me to:

>  You are not the owner, so you cannot change these permissions.

It also says that root owns the file...

Did I do something wrong with the installation for it to have done this?

I am so close to having a perfectly running distro without errors and such, but this appears... Agh... Help would be greatly appreciated!

---

### Post by XAsmodeanX on 2006-07-04
Go to Applications -> Accessories -> Terminal

Once in, type:

sudo chmod a+rw jre1.5.0_07

Hit enter, then:

rm jre1.5.0_07

Or, right click and delete the file from your desktop.

Sudo executes the chmod command as root, chmod changes the "file permissions" for the file that you are modifying.  a+rw means that All users can now Read and Write to that file.

---

### Post by Miki01 on 2006-07-04
Oh, okay, but just before I do that, would any harm be done?

---

### Post by XAsmodeanX on 2006-07-04
If it's just the file that you used to install java then you should be fine in removing it.

---

### Post by Miki01 on 2006-07-04
Okay, when I typed in your first code, I get this:

> miki@Ubuntu:~$ sudo chmod a+rw jre1.5.0_07
chmod: cannot access `jre1.5.0_07': No such file or directory


And for some apparent reason, when I go to manage attachments and click on <browse>, all my firefox browser windows close...

---

### Post by Miki01 on 2006-07-04
[QUOTE=Miki01]Okay, when I typed in your first code, I get this:



And for some apparent reason, when I go to manage attachments and click on <browse>, all my firefox browser windows close...[/QUOTE]

EDIT: I used:

> sudo nautlius

and just went to the file and deleted it from there.

Thanks for the help, though, its was greatly appreciated!

---

### Post by XAsmodeanX on 2006-07-04
Sorry, my mistake.  You need to issue this command before doing the rest.

cd Desktop/

Then continue with what I said.  Make sure to substitute the appropriate filename if the jre one that I gave is not the right one.

Edit:

Good, glad to hear you got it working.  There are many different ways to do something in Linux.  Choose the one that works best for you!

---

### Post by Miki01 on 2006-07-04
Yeah, if I got your message sooner, I would've used your method. I read that giving myself temporary 'roo-powers', that I may by accident delete an important file that I shouldn't have.

---


---
title: "[IDEA] Password instead of Action Denied"
date: 2008-07-11
forum: Desktop Environments
---

### Post by castironpants on 2008-07-11
I often get annoyed when I'm (as a normal user) trying to do something simple like drag and drop a file into a superuser folder. I drag and release and it tells me I don't have permission to do so. Fine. Instead of forcing me to open up the terminal and just do it by hand, why can't it just ask for the root password?

---

### Post by coffeecat on 2008-07-11
Not quite what you're suggesting, but if you open a terminal and 

```
gksudo nautilus
```(assuming you're using Ubuntu/Gnome) you get a file browser with root privileges. Now you can drag and drop into it without problem.

I'm presuming here that your 'open up the terminal and just do it by hand' means you are doing cp, mv and/or rm from a terminal. If you already knew this trick, then excuse me.

Another thing you could do is to set up a menu entry with 'gksudo nautilus'. Then all you need do is one click, give your password when prompted and drag and drop to your heart's content.

---

### Post by castironpants on 2008-07-11
Well, yes, I suppose that would work, but it just seems unnecessary. What is the point of giving any old user a message without giving them the means to do anything about it. Even a "Not Permitted" dialog with a button that said "Browse this folder as root" that activated that command would be an improvement.

---

### Post by coffeecat on 2008-07-11
> **castironpants said:**
> What is the point of giving any old user a message without giving them the means to do anything about it. Even a "Not Permitted" dialog with a button that said "Browse this folder as root" that activated that command would be an improvement.

Don't forget that Linux is a version of Unix and Unix-type OSs are designed to be multi-user, and that 'any old users' **are not meant to be able to fiddle around in the system**. Only the sysadmin may do that and in multi-user systems s/he doesn't hand out the root password to all and sundry. 

I guess that you, like me, are using Linux at home as the sole user and this having to put in your password all the time is irritating. But Linux/Unix wasn't designed as a single user system. If you want the security that comes with Unix, put up with the inconvenience. 

I'm sure you're aware of the difference between the sudo model that Ubuntu uses and the ordinary-user and root separate passwords that most other distros use. But one thing you may not have come across yet is that the first created user in an Ubuntu installation has administrator privileges (with their password), but that subsequently-created users do not. They cannot access system files with or without their password - **unless** the system administrator (the first user = you) gives them administrative rights.

Think about it. It prevents ordinary users from borking the system. And (hopefully) it makes you less likely to bork your own system, because it reminds you that you are in a critical area of the OS. Compare that with Windows XP.

---

### Post by castironpants on 2008-07-11
I WANT the protection. I WANT to be prompted for my password. The problem is when you try to move the file, it doesn't ask you to use superuser privileges, and that's what I think should be changed. That button I just mentioned should open the prompt for the root password.

EDIT: I think I understand what you mean, though. Such a thing would only be necessary for the root, and then they wouldn't get prompted anyway. No chance of having it as an addable plugin?

---

### Post by damis648 on 2008-07-11
> **castironpants said:**
> No, I don't think you understand. I WANT the protection. I WANT to be prompted for my password. The problem is when you try to move the file, it doesn't ask you to use superuser privileges, and that's what I think should be changed. That button I just mentioned should open the prompt for the root password.

EDIT: I think I understand what you mean, though. Such a thing would only be necessary for the root, and then they wouldn't get prompted anyway. No chance of having it as an addable plugin?

You can add a nautilus "Open as root" script if you want..
See [http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/](http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/)

---

### Post by coffeecat on 2008-07-11
> **castironpants said:**
> I WANT the protection. I WANT to be prompted for my password. The problem is when you try to move the file, it doesn't ask you to use superuser privileges, and that's what I think should be changed.

I see what you mean. The trouble is that on a regular Unix/Linux installation the system simply thinks you are an ordinary user and gives you the "You do not have permissions.." cold shoulder. What it's really telling you is to b*gg*r off. :wink: As I said before, Ubuntu is a bit different, so it does appear odd to the sole user that he/she is not prompted for a password. Actually, in some circumstances you are. When you open the package manager you are. Perhaps the devs wanted to make it just that bit more difficult to muck about in system folders - just to make people stop and think. Or perhaps it never occurred to them. There are ways of making suggestions for features to be included in future releases. Why don't you investigate this? Yours is a good idea.

> **castironpants said:**
> Such a thing would only be necessary for the root, and then they wouldn't get prompted anyway.

Not quite. It's generally considered bad practice (=inadvisable) to log in as root. Good sysadmins have ordinary accounts for logging in and then su to root in a terminal when they need to.

---

### Post by Jammy4041 on 2008-07-24
if you are using PCMan File Manager, there is an option to open the folder as root.

launch the terminal 

```
sudo apt-get install pcmanfm
```

then 

```
pcmanfm
```

then in the menu at the top, View >> Open folder as root.

BTW, there is also an option to launch the terminal as well.

Hope this helps.

---


---
title: "Authorisations"
date: 2009-02-09
forum: General Help
---

### Post by Daniel350 on 2009-02-09
I came from XP to Vista, then from Vista (out of frustration) to Ubuntu, which I am now absolutely loving... except its constant "Authorisation required" prompts.
I feel like I'm back in Vista.

Any idea how to turn these off, appears to be a part of Gnome?

---

### Post by howefield on 2009-02-09
Isn't there a tick box to remember authorisation in the dialogue box that you are referring to ?

Maybe I'm thinking of something else.

---

### Post by Yashiro on 2009-02-09
What are you doing that requires you to authorize so often?

---

### Post by Daniel350 on 2009-02-10
> **Yashiro said:**
> What are you doing that requires you to authorize so often?

Practically anything to do with settings or the admin panel. I thought logically by giving myself ticks in all authorisatiosn in the Users and Groups, and also set my user to /root group, but it still requires it whenever I install programs or update programs (doing it a lot.)

---

### Post by mb_webguy on 2009-02-10
First of all, you need to [read this]("https://help.ubuntu.com/community/RootSudo"), so you know exactly what you'd be changing and why before you decide whether you want to or not.

That page will tell you how to remove the password prompt for (gk)sudo, but I suggest before you do that you try a middle option.  You can increase the time increment before you are again prompted to enter a password.  By default, once you enter "sudo" or "gksu" to perform an action or launch an application as root, you aren't prompted again for a period of 5 minutes.  While this is pretty decent when working in the terminal, it's a bit short when working graphically, since you may easily spend 5 minutes working in one app.  To increase this time, do the following:

In the terminal, type: "sudo visudo" to edit the sudoers file.  (This is the only means of editing this file, so forget gedit for the moment.)

At the bottom of the file, add the line "Defaults:*username* timestamp_timeout=10" where *username* is your username.  You can change the 10 to any number of minutes you want.  15 minutes seems to be about right for me.  You could also set this to -1, in which case you will have free sudo use for an entire session after you enter the password once.  This is definitely *not* recommended if you tend to leave yourself logged in for long periods, and others have access to your computer.

---

### Post by Yashiro on 2009-02-10
*Some points about Linux.*

- It does not work like Windows.

- You should not be messing with the Authorizations panel, it's very rarely needed.

- You should not be adding yourself to the root group.

- All that's required is that IF you need to install an application  you enter your account password which is valid for a good few minutes. During which time you install the stuff you need.

- By adding extra authorizations and putting yourself into other user groups you are making a huge mess for yourself.

- If you really NEED to mess around every 5mins then give yourself a short password until you've finished setting everything up; then revert to something stronger.


[I]It may sound like I'm being an *** here because you're a Windows pro and how different can it be, right? It's true you may need to enter your pass alot in the beginning. Installing apps requires you to place files in critical system areas.

Trust me though, lay off messing with security options in your first few weeks, use my password tip and just roll with it. There's a few reasons Linux is so secure and you're attempting to circumvent them.:D[/I]

---

### Post by 3rdalbum on 2009-02-10
Once you have set up your system the way you want it, the only times you'll have to elevate to root are when you are installing new software or installing updates.

DO NOT turn the security system off! It is there for very good reasons. Linux has had this security system since 1991 and Unix has had it since its inception in the 1960s; it's a very time-tested security system that protects both yourself and the computer. Vista mimics the Ubuntu system *because it's a good idea* and *it works* and it's been keeping computers safe for *forty years*.

Also, some programs are designed to work within the system and will not work properly if you disable it.

---

### Post by mb_webguy on 2009-02-10
Oh, and while this may remind you at first of Vista's User Account Control, it's really nothing like it.  UAC bugs you every time an application wants to access a protected area, which seems to happen several times every time you start or use an application.  Ubuntu only asks you for authorization when you chose to do something that affects the entire system (like installing software or editing system files).  It will never pop up in normal use.

---

### Post by Ptero-4 on 2009-03-12
You might find useful to just install the apps you need all at once. This is one of the nice features of Ubuntu's package manager. It allows you to install and remove lots of apps in one single operation, so you enter your password once and it gets all installed/removed in one go. And believe me, in a few weeks, months at most you'll get used to the way linux works and you'll be wondering how you could use that bug-ridden, insecure mess of an OS that is windoze.

---


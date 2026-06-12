---
title: "Password Manager"
date: 2006-08-16
forum: Desktop Environments
---

### Post by pollian on 2006-08-16
I've pretty much migrated everything I need from Win2k to Ubuntu and I'm loving it. The question I have though is about password managers. For some time now, I've used Password Safe to keep track of my passwords in Windows. I'm not wedded to that program, but I am looking for a similar program to use in Ubuntu--something that would store my passwords with a relatively strong encryption and a single master password. A cross-platform application would be a plus (so that I could access my passwords from windows, if need be.) Any thoughts?

pollian

---

### Post by ardchoille on 2006-08-16
> **pollian said:**
> I've pretty much migrated everything I need from Win2k to Ubuntu and I'm loving it. The question I have though is about password managers. For some time now, I've used Password Safe to keep track of my passwords in Windows. I'm not wedded to that program, but I am looking for a similar program to use in Ubuntu--something that would store my passwords with a relatively strong encryption and a single master password. A cross-platform application would be a plus (so that I could access my passwords from windows, if need be.) Any thoughts?

pollian

I use Revelation as my password manager. Revelation stores the passwords in one file that is blowfish encrypted.. it's very safe in my opinion.

Revelation is in the universe repo. Enable that repo, do sudo apt-get update, and then install revelation with:

```

sudo apt-get install revelation

```

---

### Post by PhilOSparta on 2006-08-19
I use Revelation also.  One caution though.  Just today I wanted to export my password file onto a USB mem stick so I could take it on a trip.  I hit the export buttons and named it the same name that Revelation has been using.  It told me that I was going to overwrite the file and I said Yes.  Bad move!  It over wrote the file using a plain text format.  Now I have all my passwords in plain text for all to see.  The only solution was to re-enter all the passwords.  Experience is a hard teacher.

Phil
PS - I like the program.

---

### Post by MiniJames on 2006-10-08
KeePass is the perfect password solution. Runs on XP, Linux, and OSX.

[http://keepass.sourceforge.net/](http://keepass.sourceforge.net/)

They have even compiled a .deb for us ubunteros. ;p

[http://keepassx.sourceforge.net/downloads/](http://keepassx.sourceforge.net/downloads/)

---

### Post by ilikebirds on 2006-10-27
PassReminder runs under Windows and Linux. Moreoever you can use PassReminder with an USB key, so you can use a same memory stick under Ubuntu, Windows, Fedora...

You can download it at [http://eyecanseeyou.free.fr]("http://eyecanseeyou.free.fr")

---


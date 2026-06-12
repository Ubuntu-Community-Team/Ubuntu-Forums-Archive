---
title: "remote control"
date: 2008-06-27
forum: Desktop Environments
---

### Post by Capheind on 2008-06-27
Is there a good way to run initiate GUI apps from the console? Not the terminal in gnome, but an SSH session or a Alt+Fn console? This is mostly to run things in the GUI when I'm across the room SSH'd in on my laptop, or for prank purposes when family members are using the PC...

---

### Post by ebash on 2008-06-28
You can tell ssh to forward you X connections, this will let you start graphical applications on the remote machine (running locally there) but being displayed in your local computer. To enable X forwaring use the -X flag. For instance to connect to the server named 'laptop' as the user named 'bob' do the following:

```
ssh -X bob@laptop
```

Once connected, you can use the shell as usual and you can also start graphical applications. Keep in mind that to start multiple applications you need to put them to background otherwise you can run only one at a time. To put an application in background simply add '&' at the end. Example:

```
gimp &
```

If you just want to run a single application and nothing else you can put the application to execute as an arguments to ssh and there will be no shell used. For example to edit a configuration file as root (assuming that the user is allowed to execute sudo) simply do:

```
ssh -X bob@laptop gksudo gedit /etc/hosts
```

---

### Post by Capheind on 2008-06-28
Well basically I have a, company, laptop. what I want to be able to do is type 

```
Bob@Bob~> mplayer <file> [Magic something}
```

and have it open MPlayer in the running X session on my desktop. Or for that matter if I'm in a console (Alt+Fn) on my desktop and I suddenly realize I want to open firefox to a page I could do

```
Bob@Bob~> Firefox <page> [Magic something]
```

and have it up when I finish and change screens. That sort of stuff. Although it is handy to be able to forward X sessions... if only I could install linux on the laptop... :)

---

### Post by Capheind on 2008-07-04
Ok the Magic something appears to be --display :0.0 as in

```
Firefox <url> --display :0.0
```

---


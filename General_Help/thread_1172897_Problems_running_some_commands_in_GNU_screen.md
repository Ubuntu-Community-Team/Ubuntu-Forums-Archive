---
title: "Problems running some commands in GNU screen"
date: 2009-05-29
forum: General Help
---

### Post by Vunutus on 2009-05-29
Essentially what I want to do is simply get Now Playing information from Banshee from within a program running in GNU screen. 

This is simple enough, for example:

```
banshee --hide-field --query-title;
```

That works fine in any terminal and returns the name of the currently playing song. When I run it in screen, however, it returns this error:

```
Unhandled Exception: System.Exception: Unable to open the session message bus. ---> System.ArgumentNullException: Argument cannot be null.
Parameter name: address
  at NDesk.DBus.Bus.Open (System.String address) [0x00000]
  at NDesk.DBus.Bus.get_Session () [0x00000]
  --- End of inner exception stack trace ---
  at NDesk.DBus.Bus.get_Session () [0x00000]
  at Banshee.ServiceStack.DBusConnection.get_ApplicationInstanceAlreadyRunning () [0x00000]
  at Booter.Booter.Main () [0x00000]

```

I like screen but I keep running into quirkiness like this. Does anyone have any suggestions?

---

### Post by Vunutus on 2009-05-29
Bump

---

### Post by Vunutus on 2009-05-30
Alright it turns out that executing banshee commands in screen, regardless of whether or not they launch the GUI, produced the same error.

Anyone know?

EDIT: You know your problem is uncommon when you google it and the top result is a forum post you made =(

I'm thinking about just making a perl script to execute this and return the values I need instead of running them directly in screen. Could this cause any problems?

---

### Post by Vunutus on 2009-05-30
Okay this is really frustrating me. I wrote the Perl script I mentioned. Again, same as before. If I execute that perl script outside of screen, it works perfectly and returns my information. If I execute it within screen it returns the same exception I posted in the first post. That doesn't even make sense to me. I'm executing it by calling the perl program and passing it my script, that should be separate from screen. All screen should know is that a perl script is returning a string.

Is there any way to TRULY separate a script call from screen so I can get this working?

---

### Post by Vunutus on 2009-05-31
Bump again. Really want this to work.

---

### Post by Vunutus on 2009-06-01
Bump. It seems like most of the problems I have with Linux are things that nobody else is experiencing =/

---

### Post by unutbu on 2009-06-01
Yes, I wish I could help you, but I wasn't able to reproduce this problem.
Have you considered removing (or moving) your ~/.screenrc file if you have one?

---

### Post by lswb on 2009-06-01
I tried this on my system with these results: Running the banshee --query-title from an X based terminal I get results regardless of whether screen is running in the terminal or not. However, if I switch to a vt, banshee immediately stops playing, and doing the banshee --query-title gives the dbus errors regardless of whether screen is running or not. Is gnu-screen something different from the classic screen terminal program?

---

### Post by Vunutus on 2009-06-02
OK I've done some more researching.

It turns out that the exception I posted happens any time I try to launch banshee from an environment that cannot support graphical applications (screen, VT, ssh session without X forwarding, etc). This gave me more leverage to google the problem and I found a solution that involves using "dbus-launch" to get past that error. That seems to work, but the problem is I can't get it to launch banshee WITH the arguments. 

If I type:

```
dbus-launch banshee --hide-field --query-title
```

it acts as if I had only typed

```
dbus-launch banshee
```

Much closer to a solution than I was. Anyone have ideas?

---

### Post by Vunutus on 2009-06-02
Bump.

---

### Post by Vunutus on 2009-06-03
Bump

---

### Post by Vunutus on 2009-06-04
Bump

---

### Post by Vunutus on 2009-06-11
Bump.

---


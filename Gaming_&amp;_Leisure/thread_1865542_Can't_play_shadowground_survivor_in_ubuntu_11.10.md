---
title: "Can't play shadowground survivor in ubuntu 11.10"
date: 2011-10-20
forum: Gaming &amp; Leisure
---

### Post by maizuddin35 on 2011-10-20
Hi everyone. 
Anyone here played Shadowground ? or Shadowground Survivor?
Well , I face a problem that didn't give me the chance to play the game.

I launch the launcher and the click the launch button. and there is no response.

Here are the result I get from the terminal.

```
adib@maiz35:~/Games/survivor$ ./survivor-launcher 
./survivor-launcher: ./lib32/libxml2.so.2: no version information available (required by /usr/lib/libglade-2.0.so.0)
Got signal 11 at 0x1 from 0xd50b97
Aborted
```

I hope anyone here can help me out with this one. 
By the way, I'm using Ubuntu 11.10 with Ati Radeon HD 5770 
thank you in advanced.

---

### Post by thatguruguy on 2011-10-20
You forgot to mention that you're running 64-bit Ubuntu, which is probably the actual issue.

Install the ia32libs package.

```
sudo apt-get install ia32-libs
```

---

### Post by maizuddin35 on 2011-10-20
I'm running a 64bit ubuntu? I think I installed the 32bit version . how to check what version i use by the way?

thank you for the command :)

---

### Post by maizuddin35 on 2011-10-20
I have install the package lib that you told me too
but I still have the same result .

```
adib@maiz35:~/Games/survivor$ ./survivor-bin 
Got signal 11 at 0x1 from 0x880b97
Aborted
```
This is when, I directly launch the -bin file.

and this one, is like the one before.
```
 adib@maiz35:~/Games/survivor$ ./survivor-launcher 
./survivor-launcher: ./lib32/libxml2.so.2: no version information available (required by /usr/lib/libglade-2.0.so.0)
Got signal 11 at 0x1 from 0x9c3b97
Aborted
```

---

### Post by thatguruguy on 2011-10-20
> **maizuddin35 said:**
> I have install the package lib that you told me too
but I still have the same result .

```
adib@maiz35:~/Games/survivor$ ./survivor-bin 
Got signal 11 at 0x1 from 0x880b97
Aborted
```This is when, I directly launch the -bin file.

and this one, is like the one before.
```
 adib@maiz35:~/Games/survivor$ ./survivor-launcher 
./survivor-launcher: ./lib32/libxml2.so.2: no version information available (required by /usr/lib/libglade-2.0.so.0)
Got signal 11 at 0x1 from 0x9c3b97
Aborted
```

Apparently, I was mistaken.  Where did you obtain the file?  Was it through the Humble Bundle, Desura, or somewhere else?

Also, what graphics card are you using?  It won't run on intel integrated graphics.

---

### Post by maizuddin35 on 2011-10-20
I obtain the file through Humble Bundle. Well, I already installed it via ubuntu 11.04 last time with my nvidia 5400fx but now I change my card to ati radeon hd5770. And actually i have some difficulties tweaking the ati card driver. 
any ideas?
thank you again by the way :)

---

### Post by thatguruguy on 2011-10-20
Sorry it took me so long to get back to you.

Although I bought the Frozenbyte bundle, I never installed Shadowgrounds Survivor.  I now see your problem.

You need to go into the directory where you have Shadowgrounds Survivor installed, which is probably called "survivor" in your home directory.  Go into the "lib32"  directory, and delete the file named "libasound.so.2".  The program should now run.

More information about running the Frozenbyte games in Linux can be found [here]("http://frozenbyte.com/help_humble/linuxfaq.html").

---

### Post by maizuddin35 on 2011-10-20
thank you very much for the reply .
I will try on and update here later after working . thank you again.

---

### Post by maizuddin35 on 2011-10-21
I'd remove the file that you told me to do, and the game runs cleanly without any problem . 
thanks you for the help. by the way. how do you know, which part of file need to be tweak, or remove. :)
and again,, this thread is solved

---

### Post by Machinista on 2011-10-23
Thank you for this fix.  

What's changed between 11.04 and 11.10 to break shadowground games?

---

### Post by maizuddin35 on 2011-10-23
I don't know why.even there is some app in the USC can't work properly in 11.10

---

### Post by thatguruguy on 2011-10-24
> **maizuddin35 said:**
> I don't know why.even there is some app in the USC can't work properly in 11.10

Well, some of the apps in the USC are pretty old, and need to be removed.

As to this particular issue, shadowgrounds survivor ships with its own version of the alsa sound libraries, which are not completely compatible with the new system.  Removing that particular file (which forces survivor to use the native sound system) fixes the issue.

---

### Post by Fatfool on 2011-12-13
strange.  

I still get the error 

```
:/usr/local/games/survivor$ ./survivor-launcher./survivor-launcher: ./lib32/libxml2.so.2: no version information available (required by /usr/lib32/libglade-2.0.so.0)
Got signal 11 at 0xc from 0x838a30f
Aborted

```

even after removing libasound.so.2

---

### Post by maizuddin35 on 2011-12-13
have you followed everything @thatguruguy told to do?

---


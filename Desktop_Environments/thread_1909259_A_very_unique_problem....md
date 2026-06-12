---
title: "A very unique problem..."
date: 2012-01-14
forum: Desktop Environments
---

### Post by KarlEinstein13 on 2012-01-14
Ubuntu 11.10
Alright, so earlier today, I opened up the ol' Update Manager, and was informed I had broken packages, and that the manager could only perform a "Partial Upgrade". So, I ran it, and afterwards ran "sudo apt-get update" just to be safe.
A few hours later, I opened Synaptic and repaired these broken packages with their broken dependencies and the like.
<backstory>
I was running gnome-shell, with a user theme, using Ubuntu Tweak and other shell extensions. To do so, I had set up several PPA's.
I'm pretty sure these PPA's I set up may have led to my problem.
</backstory>
Then, suddenly after a reboot back into gnome-shell, I was shocked. I had lost my theme, and my background image.
Now, I'm back in Unity after backing up my data and scratching my head. I can't change my background image, and my window's themes are all messed up.

[http://oi42.tinypic.com/or43d0.jpg](http://oi42.tinypic.com/or43d0.jpg)

As you can see, I'm using the "Radiance" theme, but the space beneath the title bar is black, with a black font. This problem carried over to my login screen, with the text in the upper right corner also going black-on-black.

To fix this, I've rm -f'd my ".metacity" and my ".gnome" folders and a few others to see if it would fix it, and no dice.
I've also un-installed gnome-shell, and I'm really hoping to fix the problem in Unity first, then go back to shell.

Can anyone help me?

---

### Post by Krytarik on 2012-01-14
Please see this thread from yesterday:

[http://ubuntuforums.org/showthread.php?t=1908388](http://ubuntuforums.org/showthread.php?t=1908388)

"Unique", hehe, as if! :P

Regards.

---

### Post by KarlEinstein13 on 2012-01-15
So...is patience going to be the remedy here?
Or am I going to want to force the version of libglib2.0-0[ricotz] down?

---

### Post by Krytarik on 2012-01-15
> **KarlEinstein13 said:**
> So...is patience going to be the remedy here?
Or am I going to want to force the version of libglib2.0-0[ricotz] down?
Well, I myself would force down the versions of both (!) packages ("libglib2.0-0" and "libglib2.0-bin"), that is, download and install the previous, working versions manually, and then lock them, and try again when all the packages are updated again.

---

### Post by KarlEinstein13 on 2012-01-15
Thank you for your response, but I have one last question:

I have (in Synaptic) selected to force both packages down (libglib-2.0-0, and libglib2.0-bin) to their previous versions: 2.30.0-0ubuntu4.

Then, before I apply any package changes, a warning comes up about what packages will be removed/installed/changed, and essentially all of my applications will be removed (429), and replaced with 55 other ones.

That is a super scary warning to me. Any other assistance/thoughts?

---

### Post by Krytarik on 2012-01-15
> **KarlEinstein13 said:**
> I have (in Synaptic) selected to force  both packages down (libglib-2.0-0, and libglib2.0-bin) to their previous  versions: 2.30.0-0ubuntu4.

Then, before I apply any package changes, a warning comes up about what  packages will be removed/installed/changed, and essentially all of my  applications will be removed (429), and replaced with 55 other  ones.
That's the version in the official repos, and that's not the way I described, and how we solved this in the other thread. So please read my instructions 'a bit' more carefully! ;-) :
> **Krytarik said:**
> Well, I myself would force down the versions of both (!) packages ("libglib2.0-0" and "libglib2.0-bin"), that is, download and install the previous, working versions manually, and then lock them, and try again when all the packages are updated again.
For more clarity and for easier future reference, this is where you can download the previous, working versions of those packages, as linked to in the other thread, too:

[https://launchpad.net/~ricotz/+archive/testing/+build/3082806](https://launchpad.net/~ricotz/+archive/testing/+build/3082806)

---

### Post by KarlEinstein13 on 2012-01-15
I'm sorry that I haven't followed your instructions very well, you are still being very helpful, and thank you for your patience. I haven't much experience with Synaptic.

Now, I have downloaded:
"libglib2.0-0-dbg_2.31.80ubuntu1~11.10~ricotz0_amd64.deb", from ([https://launchpad.net/~ricotz/+archive/testing/+build/3082806](https://launchpad.net/~ricotz/+archive/testing/+build/3082806)) and when I open it from my Downloads folder, the Software Centre opens up, and I click install, but nothing seems to happen.

I've also tried "sudo apt-get install '/home/parker/Downloads/libglib2.0-0-dbg_2.31.8-0ubuntu1~11.10~ricotz0_amd64.deb'", but I get this error:

"E: Unable to locate package /home/parker/Downloads"

In the other thread, after the other user installed the previous package and locked it, their problem was fixed. I think I'm still having issues during installation.

---

### Post by Krytarik on 2012-01-15
First, one thing I didn't think of till now: If you are running the i386 version of Oneiric, you need to install the packages from here!:

[https://launchpad.net/~ricotz/+archive/testing/+build/3082807]("https://launchpad.net/%7Ericotz/+archive/testing/+build/3082807")

Second, presuming you didn't install the "dbg" and "dev" packages beforehand, the only packages you need to install are:

[LIST]
[*]libglib2.0-0_2.31.8-0ubuntu1~11.10~ricotz0_<ARCH>.deb
[*]libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_<ARCH>.deb
[/LIST]
Then, to install them you could of course try to use the Software Center, but I'd rather suggest GDebi for that, or the command line method:
```
sudo dpkg -i PACKAGE1 PACKAGE2
```
Note: If you are using GDebi or the Software Center for that, you need to install the "bin" package first, as a matter of dependency!

After that, lock their versions with Synaptic.

---

### Post by KarlEinstein13 on 2012-01-15
Thank you for still trying to help me with this. And yes, I am using the i386 version, thank you for catching that.

Okay, so I open GDebi and select the package:

"libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb"

But I get an error stating that a newer version is already installed. This is the right package, correct? I need the bin version for dependencies, first, right?

Did I miss a step?

---

### Post by Krytarik on 2012-01-15
> **KarlEinstein13 said:**
> Okay, so I open GDebi and select the package:

"libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb"

But I get an error stating that a newer version is already installed. This is the right package, correct? I need the bin version for dependencies, first, right?
Well, that's what this is all about, *downgrade*. ;-) So just go ahead with installing that package. And yeah, that's the right package, and right order.

---

### Post by KarlEinstein13 on 2012-01-15
I'm not even getting the option to confirm installation.

[http://i43.tinypic.com/warpr9_th.png](http://i43.tinypic.com/warpr9_th.png)

The "Install Package" button is grayed-out, nothing happens when I click it.

](*,)

---

### Post by Krytarik on 2012-01-15
> **KarlEinstein13 said:**
> I'm not even getting the option to confirm installation.

[http://i43.tinypic.com/warpr9_th.png](http://i43.tinypic.com/warpr9_th.png)

The "Install Package" button is grayed-out, nothing happens when I click it.
This 'pic' is indeed 'tiny'. LOL:P

But try the command line method as stated before, and if you get any error messages, post them.

---

### Post by KarlEinstein13 on 2012-01-15
Oh dang, I'm so sorry about the size of that link. Here's the full-size image: [http://oi43.tinypic.com/warpr9.jpg](http://oi43.tinypic.com/warpr9.jpg)

And I attempted the terminal method, and I regret to inform you that I got the following error message:

> parker@blackhat-HP-G72:~$ sudo dpkg -i '/home/parker/Downloads/libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' 
dpkg: warning: downgrading libglib2.0-bin from 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 to 2.31.8-0ubuntu1~11.10~ricotz0.
(Reading database ... 200780 files and directories currently installed.)
Preparing to replace libglib2.0-bin 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.31.8-0ubuntu1~11.10~ricotz0); however:
  Version of libglib2.0-0 on system is 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0.
dpkg: error processing libglib2.0-bin (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libglib2.0-bin

---

### Post by Krytarik on 2012-01-15
> **KarlEinstein13 said:**
> ```
parker@blackhat-HP-G72:~$ sudo dpkg -i '/home/parker/Downloads/libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' 
dpkg: warning: downgrading libglib2.0-bin from  2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 to  2.31.8-0ubuntu1~11.10~ricotz0.
(Reading database ... 200780 files and directories currently installed.)
Preparing to replace libglib2.0-bin  2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 (using  .../libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.31.8-0ubuntu1~11.10~ricotz0); however:
  Version of libglib2.0-0 on system is 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0.
dpkg: error processing libglib2.0-bin (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libglib2.0-bin
```
Oops, I made an error in thinking earlier :P ; since the "bin" package depends on the exact same version of the main package, you can't downgrade it first; on the other hand, if you try to downgrade the main package first, it would remove the "bin" package, of course, and in turn most probably remove some other packages as well. So the best way is to install them both at the same time, as indicated in the previously stated command; this should definitely work.

---

### Post by KarlEinstein13 on 2012-01-15
New error, assuming I ran:

> sudo dpkg -i PACKAGE1 PACKAGE2

correctly.

> parker@blackhat-HP-G72:~$ sudo dpkg -i '/home/parker/Downloads/libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' 
dpkg: warning: downgrading libglib2.0-bin from 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 to 2.31.8-0ubuntu1~11.10~ricotz0.
(Reading database ... 200780 files and directories currently installed.)
Preparing to replace libglib2.0-bin 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.31.8-0ubuntu1~11.10~ricotz0); however:
  Version of libglib2.0-0 on system is 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0.
dpkg: error processing libglib2.0-bin (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libglib2.0-bin
parker@blackhat-HP-G72:~$ sudo dpkg -i '/home/parker/Downloads/libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' '/home/parker/Downloads/libglib2.0-0-dbg_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' 
[sudo] password for parker: 
dpkg: warning: downgrading libglib2.0-bin from 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 to 2.31.8-0ubuntu1~11.10~ricotz0.
(Reading database ... 200780 files and directories currently installed.)
Preparing to replace libglib2.0-bin 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
Selecting previously deselected package libglib2.0-0-dbg.
Unpacking libglib2.0-0-dbg (from .../libglib2.0-0-dbg_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.31.8-0ubuntu1~11.10~ricotz0); however:
  Version of libglib2.0-0 on system is 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0.
dpkg: error processing libglib2.0-bin (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-0-dbg:
 libglib2.0-0-dbg depends on libglib2.0-0 (= 2.31.8-0ubuntu1~11.10~ricotz0); however:
  Version of libglib2.0-0 on system is 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0.
dpkg: error processing libglib2.0-0-dbg (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libglib2.0-bin
 libglib2.0-0-dbg

---

### Post by Krytarik on 2012-01-15
> **KarlEinstein13 said:**
> ```
parker@blackhat-HP-G72:~$ sudo dpkg -i  '/home/parker/Downloads/libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb'   '/home/parker/Downloads/**libglib2.0-0[COLOR=Red]-dbg[/COLOR]_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb**'  
[sudo] password for parker: 
dpkg: warning: downgrading libglib2.0-bin from  2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 to  2.31.8-0ubuntu1~11.10~ricotz0.
(Reading database ... 200780 files and directories currently installed.)
Preparing to replace libglib2.0-bin  2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 (using  .../libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
Selecting previously deselected package libglib2.0-0-dbg.
Unpacking libglib2.0-0-dbg (from .../libglib2.0-0-dbg_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.31.8-0ubuntu1~11.10~ricotz0); however:
  Version of libglib2.0-0 on system is 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0.
dpkg: error processing libglib2.0-bin (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-0-dbg:
 libglib2.0-0-dbg depends on libglib2.0-0 (= 2.31.8-0ubuntu1~11.10~ricotz0); however:
  Version of libglib2.0-0 on system is 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0.
dpkg: error processing libglib2.0-0-dbg (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libglib2.0-bin
 **libglib2.0-0[COLOR=Red]-dbg[/COLOR]**
```
Wrong package, buddy! ;-) You need:

"libglib2.0-0_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb"

Try again! :D

---

### Post by KarlEinstein13 on 2012-01-15
Did it work? I didn't get any errors!

> parker@blackhat-HP-G72:~$ sudo dpkg-i '/home/parker/Downloads/libglib2.0-0_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' '/home/parker/Downloads/libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' 
[sudo] password for parker: 
sudo: dpkg-i: command not found
parker@blackhat-HP-G72:~$ sudo dpkg -i '/home/parker/Downloads/libglib2.0-0_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' '/home/parker/Downloads/libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb' 
dpkg: warning: downgrading libglib2.0-0 from 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 to 2.31.8-0ubuntu1~11.10~ricotz0.
(Reading database ... 200806 files and directories currently installed.)
Preparing to replace libglib2.0-0 2.31.9+git20120113.a6e149e4-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-0_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
Unpacking replacement libglib2.0-0 ...
Preparing to replace libglib2.0-bin 2.31.8-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-bin_2.31.8-0ubuntu1~11.10~ricotz0_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
Setting up libglib2.0-0 (2.31.8-0ubuntu1~11.10~ricotz0) ...
Setting up libglib2.0-bin (2.31.8-0ubuntu1~11.10~ricotz0) ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

>crosses fingers for you to reply with "Yep, now reboot, and everything will be back to normal!"

---

### Post by Krytarik on 2012-01-15
> **KarlEinstein13 said:**
> Did it work?
Yep, this :P :
> **KarlEinstein13 said:**
> "Yep, now reboot, and everything will be back to normal!"

---

### Post by KarlEinstein13 on 2012-01-15
Good sir, I cannot thank you enough. Everything appears to be working again.

Thank you so very much.

---


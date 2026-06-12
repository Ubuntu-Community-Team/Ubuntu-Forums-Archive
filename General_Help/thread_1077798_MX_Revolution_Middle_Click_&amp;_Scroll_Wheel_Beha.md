---
title: "MX Revolution: Middle Click &amp; Scroll Wheel Behavior"
date: 2009-02-22
forum: General Help
---

### Post by trump29 on 2009-02-22
Hi all, I need help :(

I'm running Linux Mint 6 64-bit and I'm having some trouble getting my mouse (Logitech MX Revolution) to behave in Linux the way I had it set up in Windows. I've been working on the problem for about a week but everything I try runs into snags and am not savvy enough to know what to do about them (total Linux noob).

There are two things I want my mouse to do: **(1)** I want the button behind the scroll wheel (not the scroll wheel itself but the "Search" button) to behave as a middle click.** (2)** Get the scroll wheel to switch to switch between smooth scroll and ratcheted scrolling automatically.

From my searching I know that both are possible on Linux. I'll link out all the resources I've used and try and provide screenshots where I ran into trouble:

[size=5]_1st attempt - btnx:_[/size]

I read [this thread](http://ubuntuforums.org/showthread.php?p=2727025) and thought that btnx could solve all my problems. When I tried to "detect mouse & buttons" as the images below show, I couldn't get anything to detect. I later found out that Mint 6 = Intrepid and btnx doesn't work on Intrepid.

[img]http://img24.imageshack.us/img24/10/btnx1.jpg[/img][img]http://img18.imageshack.us/img18/4214/btnx2.jpg[/img]


[size=5]_2nd attempt - xbindkeys:_[/size]

The second resource I used was [this one](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/howto_logitech_mx_revolution_on_ubuntu) (skipping down to the "Hotkeys" area), and I did have some success here in binding some behaviors to other keys on my mouse. In terms of giving the search button middle-click behavior, or fixing the mouse problem no luck though. I just don't know what code I would use to tell it to do that.


[size=5]_3rd attempt - revoco:_[/size]

Using the [same resource](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/howto_logitech_mx_revolution_on_ubuntu) but skipping down to the "Scroll Wheel" section I found out how I should be able to get the scroll wheel behavior that I want, using revoco.

So I tried to install revoco using the code he gives:

> gcc -Wall -02 revoco.c -o revoco

The first problem I figured out was that he put 02 instead of O2 and that was giving me an error "unrecognized option '-02'"

The second problem, the one I can't get past, is this:

> revoco.c: In function ‘usage’:
revoco.c:489: error: expected ‘)’ before ‘VERSION’
[img]http://img124.imageshack.us/img124/5600/revoco.jpg[/img]


[size=5]_4th attempt - revoco in btnx:_[/size]

I read a comment from someone that revoco is already in btnx, and that should work, so I went back to btnx since I did successfully install it at least. In the btnx revoco tab though it says "An MX Revolution mouse has not been detected. revoco is disabled, and everything is grayed out.

[img]http://img54.imageshack.us/img54/7277/revocobtnx.jpg[/img]


[size=5]_5th attempt - begging for help:_[/size]

Please help me, this is frustrating. I'm so used to having it that if I can't get it working in Linux then I'll probably have to live in Windows :( ... it seems like it should be able to work, I'm just too nooby to figure out what I'm doing wrong.

---

### Post by NicksSpleen on 2009-02-24
I too have a mx revolution. I was sad when I updated to intrepid and btnx stop working. So I figured out a solution that combines revoco, xbindkeys, and xmacro. Unfortuantly the only button I have not figured out how to map is the search button.

Revoco will get your scroll wheel working correctly. Download revoco and extract the folder. Assuming you extracted it onto your desktop in a terminal type to build the program.

cd Desktop/revoco-0.5
make

Now the command to change your mouse button to auto scroll is: 

sudo ./revoco auto=x,y

Where the x is the speed at which to change when scrolling up and y is scrolling down. I set both to 15 but you can play around with it.

---

### Post by trump29 on 2009-02-26
Thanks very much! I'm not sure what I was doing wrong with Revoco, but that worked great!

Unfortunately I screwed up a couple buttons trying to get the search button to do what I want it to, but if I do get it figured out I'll let you know.

If anyone else has any help on the search button issue I'd greatly appreciate any help.

---

### Post by WSDsmurf on 2009-03-01
i have exactly the same issue with my 'former middle click' button now activating 'tracker search too' on my logitech... driving me batty.

i've had no luck fixing it either (noobishness also my problem)

---

### Post by knetcomp on 2009-03-08
> **WSDsmurf said:**
> i have exactly the same issue with my 'former middle click' button now activating 'tracker search too' on my logitech... driving me batty.

i've had no luck fixing it either (noobishness also my problem)

Go to System > Preferences > Keyboard Shortcuts and remove the shortcut for search.

---

### Post by cecilx22 on 2009-03-14
try installing the graphical configuration tool for xbindkeys:

```
sudo apt-get install xbindkeys-config
```

the middle button on the MX is actually seen by Ubuntu as a KEYBOARD key, NOT a mouse key.  You can use the config window to capture it (it's the XF86Search key)

the config tool makes xbindkeys pretty easy to setup, but you'll still need to understand the magic of xmacroplay.

to simulate a keyboard key press and release in xmacroplay use the following:

```
echo 'KeyStrPress <keyname> KeyStrRelease <keyname>' | xmacroplay :0
```

to do a mouse button press use:

```
echo 'ButtonPress <buttonname> ButtonPress <buttonname>' | xmacroplay :0
```

never done mouse button presses before...  don't know if buttonname should be b:3 or just 3.  play with it and get back to us!

Also, make sure to add xbindkeys to your session!

Hope this helps

-Ben

---

### Post by KamiOfTea on 2009-06-25
Thanks for that, finally got my middle click working :D.

Needed to install xmacro

```
sudo apt-get install xmacro
```Follow knetcomp's advice and disable the search short cut in System > Preferences > Keyboard Shortcuts and remove the shortcut for search.     

Run xbindkeys-config, the get key button will pick up the input from the search button.

The command to run is

```
echo 'ButtonPress 2 ButtonRelease 2' | xmacroplay :0
```The relevant lines in ~/.xbindkeysrc that xbindkeys-config generated for me were
```

#Middle Click
"echo 'buttonpress 2 buttonrelease 2' | xmacroplay :0"
    m:0x0 + c:225
    XF86Search 
```Start xbindkeys...middle click :)

---

### Post by Adrian Challinor on 2010-03-09
> **knetcomp said:**
> Go to System > Preferences > Keyboard Shortcuts and remove the shortcut for search.

Kudos given. This was the spell I needed. Thanks:D

---


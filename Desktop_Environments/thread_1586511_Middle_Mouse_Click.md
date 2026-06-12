---
title: "Middle Mouse Click"
date: 2010-10-02
forum: Desktop Environments
---

### Post by N1GHTS on 2010-10-02
Hi, I am a frequent visitor of the forum but this is my first post.

Usually someone has already answered my question but in this case I couldn't find a solution to match my problem.

My problem is that I recently discovered the hard way that my middle mouse button is mapped to the function of pasting text. This is extremely dangerous to me since I have overwritten and corrupted lots of source code that I work with and struggle for hours finding and fixing the consequences of the middle click's actions. I use the middle mouse scroll function to scroll around in NetBeans IDE, but if I accidently click down on it, then scroll to the place I wanted to get to, I won't notice what I did until its too late, and usually performing undo is not an option as I have already coded other things in the same file.

So how do I go about removing this middle click feature?

---

### Post by byStanderone on 2010-10-02
...am on karmic and took a brief check on the mouse options and did'nt find and buttons for the mouse middle button, i guess it is safer to use a mouse without it.

---

### Post by Am Elder on 2010-10-02
Hello N1GHTS,

I don't have any experience trying to do this, but I think I found [a page on the Ubuntu wiki]("https://wiki.ubuntu.com/X/Config/Input") that might help you.  It looks like it depends on what release you're running.  At a guess, you either want the section on [input configuration with udev]("https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29") if you're using Lucid or later, or perhaps the section promisingly entitled ["Example: disabling middle-mouse button paste on a scrollwheel mouse"]("https://wiki.ubuntu.com/X/Config/Input#Example:%20Disabling%20middle-mouse%20button%20paste%20on%20a%20scrollwheel%20mouse").

---

### Post by N1GHTS on 2010-10-02
[COLOR=Red]@byStanderone[/COLOR]

**> i guess it is safer to use a mouse without it.**

Sounds exactly like what an I.T. person would have said over 10 years ago. I don't mean to trump you attempt at helping me, I sincerely appreciate it, but in the modern world, replacing hardware to fix a software issue is just not an acceptable option any more... especially in a Linux platform.



[COLOR=Red]@Am Elder[/COLOR]

[COLOR=Black]I am running Ubuntu 10.04 with all the updates. The most relevant solution was the final link you posted. This is what I tried:

[/COLOR] ```

xinput list | grep 'id='

```This gave me a list of input devices. I found my mouse on the list and memorized its ID number (In my case it was id=9). Then I typed this:

```

xinput get-button-map 9

```And this was what it listed:

```

1 2 3 4 5 6 7

```So as the document pointed out, 1 corresponds to left mouse, 2 corresponds to middle mouse, 3 corresponds to right mouse... and the others are some spares I guess. So the fix is ultimately to change the 2 to something not a 2, thereby disabling the button. They recommended 0. So I did this:

```

xinput set-button-map 9 1 0 3 4 5 6 7

```The 9 is my device ID, and then the rest of the numbers is a repeat of the button numbers with 2 changed to 0. After doing that, I checked my button map again and it shows the 2 replaced with 0. Now the middle click pasting feature is gone.

Now technically this is not a solution, its just a workaround for the NetBeans IDE. Now all the other programs which I use that require the middle mouse button do not work, such as Firefox or Blender or video games or .. well anything else. 

So now I need to create two scripts that I must run every time to enable and disable the middle mouse button, which is no fun considering I switch between researching on the web at the same time as I code in NetBeans.

So If someone can find a better solution I would be thrilled to hear it!

---

### Post by Am Elder on 2010-10-03
Thanks for outlining how you did this so others can profit from your search for info.

I searched for "middle button paste" and found some interesting info.  Keeping in mind, you seem to be a more advanced user than I am, I'm pretty sure you can fix your problem by [editing Xorg.conf]("https://wiki.ubuntu.com/X/Config") [ubuntu wiki page on configuring X].  I found [a post on these forums from 2007]("http://ubuntuforums.org/showpost.php?p=2585989&postcount=4") that you might be able to copy-paste into your config file.  If I understand [how this works]("http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html#sect6") [xorg.conf manual page], to do real editing you have to make sure you're setting the [right options in the right way]("http://www.x.org/archive/X11R6.8.0/doc/mouse.4.html") [mouse driver manual page on ["]www.x.org]]("http://www.x.org).

---

### Post by efball3 on 2010-10-03
xmodmap -e "pointer = 1 3 2 4 5"

This swaps the middle and right button fuctions. You can't paste while scrolling and the paste fuction is just easier with the right button, so is using firefox.

---

### Post by byStanderone on 2010-10-04
...no problem, life might have been easier ten years ago, besides, i may be more than ten years your age.

---


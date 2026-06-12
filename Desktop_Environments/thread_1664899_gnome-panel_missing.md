---
title: "gnome-panel missing"
date: 2011-01-11
forum: Desktop Environments
---

### Post by snowmanman on 2011-01-11
I installed ubuntu netbook edition on my desktop (from the Ubuntu Software Center) to test out Unity. It looked pretty cool, but every time I went to the sidebar it flashed black. I decided I didn't want to fiddle with it too much to get it working so I uninstalled the ubuntu-netbook package. Mutter was still hanging around though (and  lot of other things I assume) so I uninstalled that as well. Now gnome-panel is gone and I don't know how to get it back. Any way to uninstall all those packages and put it back?

---

### Post by checoimg on 2011-02-24
by now you can run gnome-panel on a terminal until you solve the problem. I'm having the same problem
Have to reload windwos manager with compiz icon and run gnome-panel as I said

---

### Post by coabiguy on 2011-02-26
I have this same problem. gnome-panel is not in my search path. A whence gnome-panel returns 1.
There is no .gnome-panel directory in my home directory either

How do I get it back?

---

### Post by coljohnhannibalsmith on 2011-02-26
Hi,

I've had the same problem a number of times and in desperation reinstalled the OS, only to eventually encounter the problem again two more times, within the next several months.

After reading a variety of posts and experimenting on my own, I finally came-up with the following solution:

**If you have the 'gnome-terminal' icon displayed on the Desktop:

1. Start 'gnome-terminal.'

2. Run the following code: 'gnome-panel.'

   When the upper and lower 'panels' appear;

3. Select 'System > Preferences > Startup Applications,' then

4. Add 'gnome-panel' to the 'Startup Programs.'

When you reboot, both your upper and lower panels will load as intended.  Problem solved!

**If you 'don't' have the 'gnome-terminal' icon on the Desktop:

1. Press Alt-F2, to launch the "Run Application" window.

2. Run the following code: 'gnome-panel.'

    When the upper and lower 'panels' appear;

3. Select 'System > Preferences > Startup Applications,' then

4. Add 'gnome-panel' to the 'Startup Programs.'

When you reboot, both your upper and lower panels will load as intended.  Problem solved!

**If somehow you can't find 'gnome-panel,' or have somehow managed to uninstall it; here's another 'twist:'  (You will need an active Internet connection for this)!

1. Launch 'gnome-terminal, ' from the desktop, or with 'Alt-F2,' then

2. Run the following code: 'sudo apt-get install gnome-panel,' and let it install, then;

3. Follow the remaining steps from above.

This 'should' cover all the possible scenarios. 


It's unfortunate and strange that the file that holds this setting somehow gets corrupted.  This feature needs some kind of 'failsafe,' as this bug will render your system unusable!

---

### Post by atulsingh7890 on 2011-04-02
> **coljohnhannibalsmith said:**
> Hi,

I've had the same problem a number of times and in desperation reinstalled the OS, only to eventually encounter the problem again two more times, within the next several months.

After reading a variety of posts and experimenting on my own, I finally came-up with the following solution:

**If you have the 'gnome-terminal' icon displayed on the Desktop:

1. Start 'gnome-terminal.'

2. Run the following code: 'gnome-panel.'

   When the upper and lower 'panels' appear;

3. Select 'System > Preferences > Startup Applications,' then

4. Add 'gnome-panel' to the 'Startup Programs.'

When you reboot, both your upper and lower panels will load as intended.  Problem solved!

**If you 'don't' have the 'gnome-terminal' icon on the Desktop:

1. Press Alt-F2, to launch the "Run Application" window.

2. Run the following code: 'gnome-panel.'

    When the upper and lower 'panels' appear;

3. Select 'System > Preferences > Startup Applications,' then

4. Add 'gnome-panel' to the 'Startup Programs.'

When you reboot, both your upper and lower panels will load as intended.  Problem solved!

**If somehow you can't find 'gnome-panel,' or have somehow managed to uninstall it; here's another 'twist:'  (You will need an active Internet connection for this)!

1. Launch 'gnome-terminal, ' from the desktop, or with 'Alt-F2,' then

2. Run the following code: 'sudo apt-get install gnome-panel,' and let it install, then;

3. Follow the remaining steps from above.

This 'should' cover all the possible scenarios. 


It's unfortunate and strange that the file that holds this setting somehow gets corrupted.  This feature needs some kind of 'failsafe,' as this bug will render your system unusable!
that is good one 
thanks for this it actually worked in my case where none of pkil gnome-panel was working..
again thanks for that...

---

### Post by pbhill on 2011-04-07
My lower panel is there... I can see the Trash and an applet, but there are no indicators showing running applications. I had about 10 instances of Firefox running before I figured out why things were bogging down. How do I restore them?  Is there a way to return to "default"?

---

### Post by Copper Bezel on 2011-04-07
Just right-click the panel and select Add, then choose "Application List" (or on second thought, it might be "Window List.")

---


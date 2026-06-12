---
title: "Beryl+Fiesty=Can't resize windows easily or properly"
date: 2007-04-26
forum: Desktop Environments
---

### Post by grogger13 on 2007-04-26
I just upgrade to Fiestys and have to say its awesome and a great improvement.

The only downgrade has been the functionality of beryl.  When i upgraded i got the white screen problem so i followed a forum for fixing it.

Now i notice any time i try and resize a window i click on the corner and the mouse jumps around when moving and sometimes stays clicked on the window corner and i cant resize windows to the right size i really want.

Has anyone had this problem?

---

### Post by Pox on 2007-04-27
I haven't heard of this problem, but what was the fix you used for the white-screen problem?

---

### Post by kpel on 2007-04-27
I noticed a lot of jerky motion when resizing because of the way the window was redrawing.  Go to Beryl Settings Manager>Window Management>Resize Window>Behavior (tab) and check "Repaints the Window on Each Resize Step".

You can also change how it redraws when you're resizing.  'Normal' is always going to stutter a bit because it redraws every time the window size fits the aspect scale.

---

### Post by grogger13 on 2007-04-29
> **Pox said:**
> I haven't heard of this problem, but what was the fix you used for the white-screen problem?

I don't remember exactly how it went but there are a bunch of treads on this.  What i had to do was go into synaptic and find the beryl-core package.

Then select it and go to the menu at the top of the window where it says package->force and then select the one with the ~ in it.  

I know that is an absolutely terrible tutorial, but just search in the forums if you can't find it

---

### Post by grogger13 on 2007-04-30
I tired changing it to redraw and from normal to stretch and now sometimes it works fine,  but other times it acts exactly the same and jumps up and down and grabbs my mouse.  As Im typing this my window is resize randomly becuase it has my mouse grabbed.  I dont know how to even get it free.

I do have to say that Fiesty as destroyed alot of the nice parts of having beryl.

---


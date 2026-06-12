---
title: "Gnome &quot;Window List&quot; and also Gaim"
date: 2007-03-30
forum: Desktop Environments
---

### Post by craigyjack on 2007-03-30
Hello,
I have been studying the Gnome "window list" in the panel for a while now and I have yet to understand how exactly it is working. It seems to determine the size of the bar in the list somewhat randomly. I'm sure there is some order but I cannot see it and I am very confused on why it changes so much all the time.

First off, when opening a new window, the window list usually will not just add another bar onto the list but sometimes shorten everything up and shove all the bar onto one side. Why is it not using a uniform default size UNTIL the whole window list is used up and then resize accordingly?

This is very bad with Gaim I noticed, and this is what drove me off the edge. With Gaim running, the window list bars get real funky. They only use up like 1/3 of the alloted area when I open several im windows (I dont use tabbed iming) and the bars in the window list get tiny while there is plenty of space for the bars to expand and take up the whole window list space.

At first I thought it was just a Gaim thing, and Gaim does make it much worse, but it seems every bar in the window list ( different desktops so I observed different sets) acts strangely and I can't understand the "logic" that the window list is using to size the bars in the allocated space.
I have messed with the minimum window list size in the preferences to no ado, it normally make it even funkier.

If someone understands how the window list functions or a way to set maybe a default bar size until the whole space is filled up, or why Gaim is messing up the window list so bad, I would much appreciate it. I just don't know what is up with the window lists in my panels.

Thanks,
Craig

---

### Post by codypumper on 2007-03-30
Left to the window list are a few dots. Right click on those dots, and select preferences. You should be able to select a default min. and max. size there.

---

### Post by dbbolton on 2007-03-31
> **craigyjack said:**
> Hello,
I have been studying the Gnome "window list" in the panel for a while now and I have yet to understand how exactly it is working. It seems to determine the size of the bar in the list somewhat randomly. I'm sure there is some order but I cannot see it and I am very confused on why it changes so much all the time.

First off, when opening a new window, the window list usually will not just add another bar onto the list but sometimes shorten everything up and shove all the bar onto one side. Why is it not using a uniform default size UNTIL the whole window list is used up and then resize accordingly?

This is very bad with Gaim I noticed, and this is what drove me off the edge. With Gaim running, the window list bars get real funky. They only use up like 1/3 of the alloted area when I open several im windows (I dont use tabbed iming) and the bars in the window list get tiny while there is plenty of space for the bars to expand and take up the whole window list space.

At first I thought it was just a Gaim thing, and Gaim does make it much worse, but it seems every bar in the window list ( different desktops so I observed different sets) acts strangely and I can't understand the "logic" that the window list is using to size the bars in the allocated space.
I have messed with the minimum window list size in the preferences to no ado, it normally make it even funkier.

If someone understands how the window list functions or a way to set maybe a default bar size until the whole space is filled up, or why Gaim is messing up the window list so bad, I would much appreciate it. I just don't know what is up with the window lists in my panels.

Thanks,
Craig
i know what you're dealing with. and you are not losing your mind - the window list is very unpredictable. i have no idea why, or what to do about it, though :/

---

### Post by craigyjack on 2007-04-01
> **codypumper said:**
> Left to the window list are a few dots. Right click on those dots, and select preferences. You should be able to select a default min. and max. size there.

I have already messed with the settings in preferences, I mentioned that in the original post. That does not change the weirdness that the window list does.

[QUOTE=dbbolton]i know what you're dealing with. and you are not losing your mind - the window list is very unpredictable. i have no idea why, or what to do about it, though :/[/QUOTE]

Yeah, I guess I will just have to deal with it for now.
I was just wondering if anyone on the forums knew what the deal was with the window list. O well, no biggie. Maybe it will be better in Feisty Fawn, although I don't know if the GDM will change at all, so maybe not.

Thanks,
Craig

---

### Post by codypumper on 2007-04-01
Sorry I didn't read your first post thoroughly.
I too have a awkward moments with the windows list, and I think it has something to do with the amount of text in the header of the first window.  I believe it uses it as a default of some sort for the size of all the windows, although I'm not sure.

---

### Post by craigyjack on 2007-04-01
You are right. Except it is not the first window, it is any of the windows. I was experimenting with Firefox as one of the windows and switching between tabs that had long titles and short titles. It seems the window list uses that length as a general default for all the the window bars in the list.

I think that is a really weird thing to base the size of all the windows off of, but yeah. I found that moving the min list size in preferences pretty high made it a lot better with a few windows open (whereas before they would become tiny if the title of the windows were small). I took my min size up to 400. It is still not perfect or anything, and now when only window is open the bar for that window is huge lol.

That just doesn't seem like a good thing to base the size of the bars off of, because it is always going to be changing and the bars moving all the time, especially if using tabs in firefox, each time you go to a different tab, your window bars in the window list or gonna shift in size. hmmm, maybe that will be fixed in Gnome sometime, because it just seems weird and functions weird.

---

### Post by codypumper on 2007-04-02
I suppose it would be best to let a developer know, yes?

---

### Post by Kent84 on 2007-04-21
Hi,

I too think that the windows list in Gnome is quite stupid... here is how it works:

The min & max numbers determine the minimum and maximum size (in pixels) for the entire Window List bar. The width of each tab is determined by the max list width divided by the number of tabs required (only if this is greater than the min list width). For example...

If you have min = 20, max = 100 and you have two tabs then each tab will be 50 wide. If you have min = 70, max = 100 and two tabs, then each tab will be 70 wide and thus only 1 and a fraction of a tab will fit on your list bar.

I find the behaviour annoying and ugly if you only have one tab open. I wonder if anyone knows of a way of customising this so that all tabs are a set size unless it will not fit in the space available for the windows list?

---

### Post by gantengx on 2007-04-24
Yeah, i hate the window list in gnome too. I find it's irritating and inconsistent. Very bad implementation of gui actually. I hope gnome will fix it in next release. I've been waiting for it to be fixed since gnome 2.8 and still the same, no difference.

And to be honest, it was the window list that really holds me back to switch to linux before.. i really hope they gonna fix it...

---

### Post by Jhongy on 2007-04-24
+1, I agree the list is rather irritating and ugly.

On a related note, does anyone know how to specifically skin those tabs? I've extracted some nice  images for them from a theme, but I don't want to apply the whole theme; I just want to alter those tabs.

---


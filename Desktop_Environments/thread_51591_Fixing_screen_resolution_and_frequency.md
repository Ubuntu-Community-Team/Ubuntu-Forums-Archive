---
title: "Fixing screen resolution and frequency"
date: 2005-07-24
forum: Desktop Environments
---

### Post by yengamatic on 2005-07-24
Hehe, another problem (i didn't want to put it in the same thread).

gnome starts with 1280 resolution at 60hz, but i want it to be 1024x768@85Hz. In Change screen resolution app i choose to fix it for my computer, but when i restart it remains the same 1280.
I installed nvidia drivers and modified xorg.conf so 1024x768 is the first mode for the default depth mode. It still uses 1280 when I restart. What can i do?

---

### Post by Perfect Storm on 2005-07-24
You could try to remove: 

Modeline &quot;1280x800@60&quot; 83.91 1280 1312 1624 1656 800 816 824 841

in Xorg.conf file and see if it helps. But the ultimate would be to have your monitor specs and modify HorizSync and VertRefresh (NB: Do this with caution, doing it wrong and you'll blow up your monitor)

Ps. make sure to make backup of the xorg.conf file before messing around with it.



.:=The AI Dude=:.

---

### Post by Ruskie on 2005-07-25
[QUOTE=Artificial Intelligence]You could try to remove: 

Modeline &quot;1280x800@60&quot; 83.91 1280 1312 1624 1656 800 816 824 841


.:=The AI Dude=:.[/QUOTE]

Hi, I have the same problem.
Removing this line doesn't work as I want. Probably it DOES set 1024x768 as default screen resolution, true, but now 1280x800 isn't available at all. That is, you can't go to that resolution even if you want. That's not what I would like to obtain.

Another tile of the puzzle: I noticed that if I move 1280x800 to the end of the list, the start resolution of the screen is actually 1024x768 (as me and yengamatic would like). It does work, therefore, but the Desktop DIMENSION still stays at 1280x800. This way it is bigger than the screen resolution, and it is "scrollable". Does it make sense? If yes, how can I change the Desktop dimension too?

Thanks
Marco

---

### Post by Ruskie on 2005-07-26
[QUOTE=Ruskie]Hi, I have the same problem.
Removing this line doesn't work as I want. Probably it DOES set 1024x768 as default screen resolution, true, but now 1280x800 isn't available at all. That is, you can't go to that resolution even if you want. That's not what I would like to obtain.

Another tile of the puzzle: I noticed that if I move 1280x800 to the end of the list, the start resolution of the screen is actually 1024x768 (as me and yengamatic would like). It does work, therefore, but the Desktop DIMENSION still stays at 1280x800. This way it is bigger than the screen resolution, and it is "scrollable". Does it make sense? If yes, how can I change the Desktop dimension too?

Thanks
Marco[/QUOTE]
 Ok, I've done some experimenting last night, and here's what I guessed.
Let's think to your monitor as a window, a viewport on a desktop. That is, consider the screen and the desktop you can see in it as 2 separate things.
The desktop has a size, and the monitor has a resolution.
If you increase the desktop size, you increase the number of pixels it is made of, while if you increase the monitor resolution you increase the number of pixels it is subdivided into (i.e. the phisical size stays the same, the number of pixel varies). Until now it's just basic concepts.

Now, when Desktop size and monitor resolution are the same (e.g. 1280x800) there is no problem: each pixel of the desktop is mapped 1:1 in a pixel of the monitor, so the whole desktop is visible.
When you have a monitor resolution smaller than desktop size (e.g. monitor 1024x768, desktop 1280x800), there are portions of the desktop that aren't visible in the viewport, and you have to scroll to see them.
That's what happens to me and (I presume) yenga in linux.

When you change resolution in Windows, you don't notice anything because when you decrease monitor resolution the desktop is shrinked as well (that's why icons often clutters). When you change resolution in Gnome, it isn't, so there are part of the desktop that are out of the viewport.

As a matter of fact, when you modify xorg.conf so 1024x768 is the first mode, it affects the *monitor resolution*, but the *desktop size* stays the same.
If you use Ctrl-Alt-+ and Ctrl-Alt-- you change monitor resolution, so you can revert back to the 1280x800 resolution and see the whole desktop.
If you use instead the "Screen resolution" link in Gnome -> Preferences, you actually change Desktop size and if applicable monitor resolution. Proof of this is that if I change "Screen resolution" when I started 1280x800, the monitor flickers as it adapts to the new resolution, while if I started in 1024x768 (and desktop still 1280x800), and use "Screen resolution" to set the desktop to 1024x768 as well, the monitor doesn't flicker because it is ALREADY in that resolution... Gnome simply shrinks the desktop size in that case.

I hope I made myself clear, perhaps I've been not... :P
However, for those brave enough to follow me until here, the idea of putting "1024x768" in first place in xorg.conf does work... partially: it set the monitor default resolution. What I (we?) need is now a way to set the desktop default size.
Any ideas?

Thank you everyone for helps and patience!
Marco

---

### Post by yengamatic on 2005-07-26
After editing xorg.conf and rebooting a bunch of times I went to bed. Next morning the resolution and frequency worked fine :S I dunno what happened but now it just works hehe

---

### Post by Ruskie on 2005-07-26
[QUOTE=yengamatic]After editing xorg.conf and rebooting a bunch of times I went to bed. Next morning the resolution and frequency worked fine :S I dunno what happened but now it just works hehe[/QUOTE]
 Aaargh!!!
It can't be that way!!! :)
Meanwhile, I found something related to "Virtual" keyword in xorg.conf
I'll try that when I get home from work...

---

### Post by Ruskie on 2005-07-26
Hey, you won't believe this one.. This evening, I started Gnome again and... it works!
Well, actually, "my desktop" works. That is, once I log in (I have graphical login enabled) the desktop is shown at the correct resolution and it has the correct size...

But the login screen, instead, is displayed at 1024x768 and it has a size of 1280x800. Therefore, the login screen is scrollable (that is ugly).
Does anybody know how to avoid it?

---

### Post by GreatBunzinni on 2005-07-26
[QUOTE=Ruskie]Hey, you won't believe this one.. This evening, I started Gnome again and... it works!
Well, actually, "my desktop" works. That is, once I log in (I have graphical login enabled) the desktop is shown at the correct resolution and it has the correct size...

But the login screen, instead, is displayed at 1024x768 and it has a size of 1280x800. Therefore, the login screen is scrollable (that is ugly).
Does anybody know how to avoid it?[/QUOTE]
 My problem is exactly the opposite. When I install the nvidia drivers, the only screen resolution which is available is the 1280x768 while my default screen mode (laptop) is 1280x800.

It would be nice that this could be easily tweaked.

---

### Post by Ruskie on 2005-07-26
[QUOTE=GreatBunzinni]My problem is exactly the opposite. When I install the nvidia drivers, the only screen resolution which is available is the 1280x768 while my default screen mode (laptop) is 1280x800.

It would be nice that this could be easily tweaked.[/QUOTE]
 Uhm... Weird... Perhaps for your Card the 1280x800 mode is not recognized?
You could try to manually put it in the xconf.org file, but if manually tweaking nv driver setting is involved, I can't be of any help... :(
Sorry!

---

### Post by GreatBunzinni on 2005-08-01
[QUOTE=Ruskie]Uhm... Weird... Perhaps for your Card the 1280x800 mode is not recognized?
You could try to manually put it in the xconf.org file, but if manually tweaking nv driver setting is involved, I can't be of any help... :(
Sorry![/QUOTE]
The problem is that with the default xorg drivers, everything works perfectly. The shit hits the fan when the NVidia drivers are installed. It is really weird because xorg.conf is virtually the same ("nv" changes to "nvidia").

---


---
title: "putting desktop icons in specific places"
date: 2020-03-18
forum: Desktop Environments
---

### Post by Skaperen on 2020-03-18
when i create new icons for my desktop, it packs them to the left.  when i login, it repacks them in the order sorting the file names in [COLOR=#ff0000][FONT=courier new]**~/Desktop**[/FONT][/COLOR].  i would rather put each icon in a specific place around the desktop display and have them stay in that position.  how can i do that?  which desktop environments can do this?

---

### Post by TheFu on 2020-03-18
fvwm can. every icon can be specifically placed on any workspace, and position.

---

### Post by Skaperen on 2020-03-19
any way to do it in xfce?

---

### Post by tea for one on 2020-03-22
> **Skaperen said:**
> any way to do it in xfce?

Which version of Xfce are you using?

Version 4.14 holds the icons in place after rebooting.

---

### Post by ajgreeny on 2020-03-22
I used to have this problem when I used desktop icons and solved it by making the text files in /home/<user>/.config/xfce4/desktop/icons* immutable.
Use ```
sudo chattr +i /home/<user>/.config/xfce4/desktop/icons*
```
Should you want to change anything you will have to remove that immutable flag with ```
sudo chattr -i /home/<user>/.config/xfce4/desktop/icons*
```
I haven't used desktop icons for a long time now as I have a vertical panel on the left side of my screen full of launchers; much tidier and easier to manage.

---

### Post by Skaperen on 2020-03-22
> **tea for one said:**
> Which version of Xfce are you using?

Version 4.14 holds the icons in place after rebooting.


*sigh* 4.12

---

### Post by Skaperen on 2020-03-22
> **ajgreeny said:**
> I used to have this problem when I used desktop icons and solved it by making the text files in /home/<user>/.config/xfce4/desktop/icons* immutable.
Use ```
sudo chattr +i /home/<user>/.config/xfce4/desktop/icons*
```
Should you want to change anything you will have to remove that immutable flag with ```
sudo chattr -i /home/<user>/.config/xfce4/desktop/icons*
```
I haven't used desktop icons for a long time now as I have a vertical panel on the left side of my screen full of launchers; much tidier and easier to manage.

tell me more about the vertical panel.  that sounds like something i  gave up on a while back.  can i put text there instead of icons?  can i  make it slide out only when the mouse point approaches or hits the left  side?

*edit*:

can i have one one the left and a different one on the right at the same time?
can i set the font and/or font size?
does it handle Unicode/UTF-8?

---

### Post by ajgreeny on 2020-03-23
> 1- Can i put text there instead of icons? can i make it slide out only when the mouse point approaches or hits the left side?
2- Can i have one one the left and a different one on the right at the same time?
3- Can i set the font and/or font size?
4- Does it handle Unicode/UTF-8? 
1- You can choose to use a label instead of an icon for launchers but the panel will then need to be wide enough to show the labels which may be a lot wider than you want, but the panel on the side, just like that at top or bottom can autohide (show only when the mouse pointer goes into it).
2- You can put a panel at any one, two, three or all of the four sides of the screen if you wish.
3- Not sure about that; I use all icons.
4- No idea, nit sure exactly what you mean, but not applicable for me as I use icons.

See screenshot for the way I use this.

---

### Post by Skaperen on 2020-03-24
what needs to be done to set this up?  is it an application program that runs?  if it is written in python that would be super awesome.  if it is written in nodejs that would be fine.

the problem i have is that many of the things i would have are like things, close enough to use the same icon.  i have the same terminal icon and have named if (the words that show up under the icon) according to which user it switches to.  so the icon i useless.  it is the words that matter.

---

### Post by webaake on 2020-03-24
Xfce4-panel supports UTF8 and you can have as many panels on screen as you like. And place them almost where you like. You can either go to Settings -> Panel -> click on the plus sign besides "Panel 0" to add a new panel. Or just right click on your present panel and go to Panel settings (you'll end up in the same settings window). Panels are numbered 0,1,2 and so on.

---

### Post by Artim on 2020-03-24
> **webaake said:**
> Xfce4-panel supports UTF8 and you can have as many panels on screen as you like. And place them almost where you like. 

Now there's an idea!  Make auto-hiding panels, put the icons in whatever order you like, put the panels wherever you like, and bingo!  Or just wait for Xubu 20.04.

---

### Post by Skaperen on 2020-03-24
so let's start with a very simple setup, on theft, with just one launcher,  i copied an icon to file ~/firsticon.jpg.  where should i copy it (again) to?  i want this icon to execute the command "/usr/bin/dm-tool switch-to-user skaperen".  how do i set this up?  do i need something like a .desktop file?

---

### Post by ajgreeny on 2020-03-24
Right click in your current panel and choose **Panel Preferences**.
At the top beside the dropbox with **Panel 0** click the green + which will give you a second small empty panel somewhere on the screen.
.
Right click in that empty panel and click **Panel Preferences** again to move that panel to where you want it by deselecting the **Lock Panel** if needed and dragging it to the chosen place. Set the autohide if that's what you want, the size etc etc, then right click again, click on **Add new items**, highlight launcher and add as many times as you need launchers.

At this stage all launchers will be empty so right click each, click **Properties** and click on the + to add an item to the launcher.  This will bring up the full list of applications on your system. Click the one you want in that launcher.  Repeat that sequence for all the other empty launchers.

To use text rather than an icon choose **Advanced** in the launcher properties and select **Show label instead of icon**.

---

### Post by him610 on 2020-03-24
I moved (dragged it with mouse) Trash icon to lower right corner, rebooted, Trash icon remained on lower right corner.
I moved Home, File System, and two disk icons to upper right in a column extending downwards, rebooted, all icons remained in place in upper right corner.
What is the issue?

Update: Icons still on the right side where I placed them yesterday. By the way. my xfce = xfce4/focal,focal 4.14

---

### Post by ajgreeny on 2020-03-25
The issue is, I think, that for Skaperen, as for me in past usage of desktop launchers, they often did not stay where I put them.

---

### Post by webaake on 2020-03-25
> **Artim said:**
> Now there's an idea!  Make auto-hiding panels, put the icons in whatever order you like, put the panels wherever you like, and bingo!  Or just wait for Xubu 20.04.

Yeah, another Xfce fan, like me! When Canoncial started with Unity in 1939, I went to Xfce (Xubuntu and Arch and others). Never looked back. The new 4.14 seems fully GTK3 comaptible and works great! You can upgrade to 4.14 in 18.04, but it's not a walk in the park. ;):KS

---

### Post by ajgreeny on 2020-03-25
> **webaake said:**
> Yeah, another Xfce fan, like me! When Canoncial started with Unity in 1939, I went to Xfce (Xubuntu and Arch and others). Never looked back. The new 4.14 seems fully GTK3 comaptible and works great! You can upgrade to 4.14 in 18.04, but it's not a walk in the park. ;):KS
Slightly off topic I realise, but did you do this using the jonathonf ppa at [https://launchpad.net/~jonathonf/+archive/ubuntu/xfce-4.14?field.series_filter=bionic](https://launchpad.net/~jonathonf/+archive/ubuntu/xfce-4.14?field.series_filter=bionic) ?

I use several PPAs without problems, and I won't try this at present but might when I install 20.04 after release, this being my main machine. I might just give it a try on a laptop I use to play around on.

---

### Post by webaake on 2020-03-25
> **ajgreeny said:**
> Slightly off topic I realise, but did you do this using the jonathonf ppa at [https://launchpad.net/~jonathonf/+archive/ubuntu/xfce-4.14?field.series_filter=bionic](https://launchpad.net/~jonathonf/+archive/ubuntu/xfce-4.14?field.series_filter=bionic) ?

I use several PPAs without problems, and I won't try this at present but might when I install 20.04 after release, this being my main machine. I might just give it a try on a laptop I use to play around on.

No, I didn't try that PPA (wish I did) I tried the xubuntu-dev PPA. But no updates presented themselves on my 18.04 Xfce 4.12 system. So I downloaded the Xfce deb packages for 19.10 and installed them manually, including almost all dependencies. A tall order since you must install them in the right order including the respective dependencies. I still have an issue with app-menu-gtk, but the system works and is stable. I wouldn't do this on a production system and I can't recommend it. But it is doable.

EDIT: Yay!! Just tried the jonathon PPA and it seems 100% okay! I'm sceptical about 19.10 and 20.04 and waiting to see what the future will bring.

---

### Post by ajgreeny on 2020-03-26
I gave the ppa a try on my laptop with Xubuntu-bionic and it certainly updated mostly without a problem.

However, there were a few packages that I use, eg, ***xfce4-mailwatch-plugin*** and ***xfce4-weather-plugin***, that wre not available in the ppa, so having tried it for a day, without too many problems I accept, I removed it using ppa-purge which successfully downgraded all packages back to the versions they were before, all of which are working fine for me.

---

### Post by Skaperen on 2020-03-26
4.14 supposedly does this.  4.12 does not.

i have my own icons in ~/Desktop/ each named <whatever>.desktop.  they don't stay where i put them.  normally the ones in ~/Desktop/ are sorted and are appended to the default icons in sorted order.  i have established a NN-<whatever>.desktop naming scheme to let me give them meaningful names and still control the order (NN).  i must fill each column before any go to the next column.

yet, even with all that, sometimes the icons get scattered around in random ordered, packed on the left.  i have a script that moves them all into a temporary directory then moves them all back, in sorted order with a 1/4 second time delay between each.  that gets them back in the correct order.  one time when this happened, i left them in the random order and rebooted.  they stayed in the exact same random order.

it would be nice to position certain icons in certain places.  for the icons i create, it would be nice to have a parameter to let me specify the position for that one, preferably in pixel resolution or finer or as a ratio of a specified resolution, like: position=216/1920,324/1080

---


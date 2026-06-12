---
title: "Noob trying to install themes help please."
date: 2008-12-17
forum: General Help
---

### Post by animeboy1984 on 2008-12-17
Hey everyone, first let me say i am glad to be joining the linux community. I just finished installing unbuntu 8.04 yesterday, it has gnome 2.22.3 with it. I am trying to get my desktop to look like a theme i found online, the theme is on this link  [http://sen7.deviantart.com/art/Screenshot-2008-11-07-102876052](http://sen7.deviantart.com/art/Screenshot-2008-11-07-102876052)  I am really lost on how to get everything working right. I have tried downloading the theme, all the individual items but have no clue on how to make it so they all pop up and mesh together like it looks on his theme. Also when i downloaded his "Mira" theme that he made i was never able to extract it to the usr/theme (not sure if thats right i have the file location wrote down) it would always give me an error or just simply not extract and install *sigh*. Any help would be great, i am trying to give linux a shot and if i could get my desktop to look like his that would be a great start, oh and i did manage to get the 3d cube desktop thing to work so i am not 100% lost heh. I will keep an eye on the forum or if anyone really wants to help me out you can hit me up on Aim (pidgin) @ Animeboy1984 , or i will check back here, i appreciate it. 
-chris:confused:

---

### Post by Wartender on 2008-12-17
ok... lemme see, i'm going to post one thing, then edit for the rest one by one.
Theme: i suggest you download fusion-icon from synaptic, along with emerald, after that open fusion-icon Applications->system tools->fusion-icon, and set emerald as your window decorator, then install the theme (i believe you just drag the compressed file onto the emerald theme manager window (system->preferences->Emerald theme manager)), set it, and you should be good to go.
edit #1:
icons: download the compressed file, go to your home directory (/home/<username>, and click ctrl+h to show hidden files, and extract the folder you downloaded into your .icons directory, then open System-preferences-Appearance and click customize and set the icons.

conky: download conky from synaptic, and in your home, press ctrl+h again, and switch the .conkyrc (or add it if it's not there) with whatever text file you downloaded

font: not sure.

wallpaper: download it and in appearance-background tab, add button, and select the image.

phew. hope this helps.

---

### Post by animeboy1984 on 2008-12-17
wow thank you very much for taking that time and doing that for me i am going to go and start doing that now and i will let ya know in a few how it goes :) thanks again hopefully my next reply will be it worked lol :)

---

### Post by Wartender on 2008-12-17
haha you're welcome (i actually really enjoy helping people like this so it's no big deal), hope it works, if there's anything that doesn't just say so!

---

### Post by Ivo Moelans on 2008-12-17
You've choses a rather complicated (well, it was *made* complicated by the author) theme. You'll find themes that are much easier to install on [http://www.gnome-look.org/]("http://www.gnome-look.org/").
Let's begin with the gtk theme. Put the file *Mira_by_sen7.gz* on your desktop, right click on it and select *Extract here*. That gives you a file called *Mira_by_sen7*. Repeat on this file. That gives you a directory *Mira_by_sen7_FILES*.
In this directory are two subdirectories. For simplicity's sake let's begin with *Mirav2*. Copy this directory to your desktop, open it and **move** *Mirav2.emerald* to your desktop. Close the directory, right click on it (still *Mirav2* and select *Create Archive...*. In the window that opens, make sure that the extension is *.tar.gz*. This gives you a file called* Mirav2.tar.gz*.
In the Main Menu go to *System&#8594;Preferences&#8594;Appearance*. In the window that opens you can drag and drop your file.

Themes you download from the link I gave you usually are ready tot d&d in the Appearance Preferences window. You were just unlucky to have chosen a theme that was constructed in such a complicated way.

See how it goes and if you want I'll talk through the other things.

Good luck!

---

### Post by Wartender on 2008-12-17
yes that's probably a better explanation for the theme (i don't use emerald so...)

---

### Post by Ivo Moelans on 2008-12-17
Our reactions seem to have crossed each other... and thanks for the compliment.

---

### Post by Wartender on 2008-12-17
haha no problem, i can't remember how installed the theme into emerald when i used it that on time so i'm a little rusty on the topic haha

---

### Post by animeboy1984 on 2008-12-17
well unfortunately either way worked :(, when i load up the emerald manager and i load up the mira theme i can see where it actually shows "Mira2" and has a bunch of info regarding what theme it is etc etc but there is no button to apply...only the top 4 (clear refresh delete importm and quit at the bottom. I have double clicked it, right clicked it, hit quit and come back its still there but nothing changes :( any idea?

---

### Post by Ivo Moelans on 2008-12-17
Normally, in Emerald Theme Manager, when you click (simple click, no double or right clicks) upon the theme it applies itself immediately to the window borders.
Don't confuse this with GTK (which I explained earlier). Emerald themes the borders of windows and nothing else. GTK themes everything in windows, except the borders (and the icons of course).

---

### Post by pirattrev on 2008-12-17
The thing i don't know how to do is get those cool widget things, like weather and such, I'm pretty positive those aren't conky

---

### Post by Ivo Moelans on 2008-12-17
You probably mean screenlets. I think they are in the repositories of Intrepid (maybe you'll have to activate Universe). *System&#8594;Administration&#8594;Synaptic Package Manager*. There go to *Settings&#8594;Repositories*. Make sure that *Community-maintained Open Source software (universe)* is checked. Reload. Search for 'screenlets'. Right click and select *Mark for Installation*, then press *Apply*. Once installed you'll find them in *Applications&#8594;Accessories&#8594;Screenlets*
This link gives you the FAQ: [http://www.screenlets.org/index.php/FAQ]("http://www.screenlets.org/index.php/FAQ")

---


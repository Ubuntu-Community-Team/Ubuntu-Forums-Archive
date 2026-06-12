---
title: "Installing Themes"
date: 2009-08-22
forum: Desktop Environments
---

### Post by livetofly on 2009-08-22
Can anyone tell how to get past this error when trying to install new themes. I had no problem installing these themes in 8.04. I am now using 9.04. eg.

Installation for theme "Linux-Mint-multi-glass" failed.
       Can't move directory over directory

Where are the themes installed and how can i remove them.

---

### Post by AmerNewbieInDE on 2009-08-22
hidden folders in your home directory

---

### Post by VCoolio on 2009-08-22
Themes are either in /usr/share/themes or in ~/.themes. Apparently the theme is already installed, or at least there is a folder with the same name. Open nautilus to delete a theme in .themes, just delete the folder. For /usr/share/themes you need root permissions, but there are only the default ubuntu themes there, unless you installed themes from the repositories or with a .deb file.

---

### Post by Stevie78 on 2009-08-22
I have exactly the same problem, only that in the hidden themes folder there is no file of that themes name. Also nothing similar. And - I can choose from themes in Appearance which are not displayed there.

Is there another folder apart from those two?

Also in usr/share/themes I have an empty folder called 'metacity-1' without any parent directory. And I cant delete it. Is that the unfinished installation from the theme that wont install because it already exists somewhere?

---

### Post by VCoolio on 2009-08-22
> **Stevie78 said:**
> I have exactly the same problem, only that in the hidden themes folder there is no file of that themes name. Also nothing similar. And - I can choose from themes in Appearance which are not displayed there.

Is there another folder apart from those two?

Also in usr/share/themes I have an empty folder called 'metacity-1' without any parent directory. And I cant delete it. Is that the unfinished installation from the theme that wont install because it already exists somewhere?

No other folder, at least not for gtk / metacity themes. What theme are you trying to install? Do you have a link?

And I also have an empty metacity-1 folder, don't know where that comes from. Don't sweat it, no harm in leaving it there.

---

### Post by livetofly on 2009-08-23
I have checked the folders /usr/shares/themes non of the themes i have loaded are in this folder. Are they stored some where else. This is so frustrating!!!

---

### Post by Stevie78 on 2009-08-23
Yeah its the Gion theme from art.gnome.org

I already know how the problem came about: I installed it through System > Preferences > Art Manager and then I was asked 'Do you want to apply the theme now?' and I clicked no (thinking I could do that later)

I installed another theme (from the same website in the same format) exactly the same way but then chose to apply it immediately - and it worked fine. I can now select and deselect it in Sys > Pref > Apperances as I like.

All I need to find is the folder where the Gion theme is now so I can delete it (and install it the way I did with the other one)

---

### Post by VCoolio on 2009-08-23
Ah, Gion is an icon theme. They go in /usr/share/icons or ~/.icons. It should show up when you click "customize" in the appearance preferences window and then search in the icon tab. Clicking "no" is perfectly ok, that is not (should not be) the problem.

@livetofly: go to your home folder, hit ctrl+h and find the .themes and .icons folder. 

Fyi, gdm-themes are for login windows only and go in /usr/share/gdm/themes and can be chosen in system > admin > login window. Beryl / emerald window borders need to be imported with emerald theme manager and will be extracted in ~/.emerald/themes.

---

### Post by Stevie78 on 2009-08-23
> **VCoolio said:**
> Ah, Gion is an icon theme. They go in /usr/share/icons or ~/.icons. 

Its there. Problem solved.

However the other theme I installed and applied immediately also was an icon theme but shows up among the other complete themes (as well as an option for icons only). Not a problem though...the options for customizing are the same.

Thanks for your help :)

---

### Post by livetofly on 2009-08-23
Ok thanks found the files location, deleted them and installed, some don't install properly though as they need some icon themes installed as well, but at least i can carry on, i am determined to make Linux my main OS.

---

### Post by VCoolio on 2009-08-23
> **livetofly said:**
> Ok thanks found the files location, deleted them and installed, some don't install properly though as they need some icon themes installed as well, but at least i can carry on, i am determined to make Linux my main OS.

Good. You can ignore the icon theme warning, it's a tip by the author of the theme which will work fine without it. You can probably find the icon theme it's complaining about at gnomelook.org. If you want to get rid of the warning, edit the index.theme file inside the theme directory. Replace the line with IconTheme by an icon theme of your choice.

---


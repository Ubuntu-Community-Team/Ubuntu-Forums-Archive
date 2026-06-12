---
title: "What better to use, ubuntu of xubuntu?"
date: 2009-02-26
forum: General Help
---

### Post by Gamak on 2009-02-26
I thought that, seeings i couldn't answer it, i'd come here and ask you guys, as it seems this is the only place that you can get solid answers. I was wondering, as the heading says if i should use ubuntu or xubuntu, and what are the pros and cons of each? Like mercury messenger for example i was reading download page and the only linux base i saw was for debian/ubuntu for example. so i just wanted to know what each has that the other doesn't.

also, need help switching from XFCE to Gnome? if i'm even asking the correct question here Lol. XFCE all have the same themes, when GNOME has much better themes that i want to install but my system won't let me. maybe i'm doing it wrong, i don't know. 

Please reply :) Thank you in advance.

---

### Post by albandy on 2009-02-26
XFCE is a light desktop environment, so you can use it in slow computers, also you can use it in newer computers.

Gnome is a heavy desktop environment with a lot of usefull utilities.

For exmaple:
I use xubuntu on my old P-III notebook with 256 MB of RAM
and I use ubuntu in my new dual core notebook with 2GB of RAM

Also you can install xfce in ubuntu without problems and test both, gnome and xfce

---

### Post by Gamak on 2009-02-26
ty, i've been having a lot of trouble with themes and such. the tarball files that come with some, i can't get them to install! or other such files as .gz . when i open terminal and type in the code that i'm supposed to, it says that the files cannot be found! and i have them on my desktop! any help with that? 

having loads of trouble Lol. but i still love linux more than windows Lol.

---

### Post by linuxisevolution on 2009-02-26
> **Gamak said:**
> I thought that, seeings i couldn't answer it, i'd come here and ask you guys, as it seems this is the only place that you can get solid answers. I was wondering, as the heading says if i should use ubuntu or xubuntu, and what are the pros and cons of each? Like mercury messenger for example i was reading download page and the only linux base i saw was for debian/ubuntu for example. so i just wanted to know what each has that the other doesn't.

also, need help switching from XFCE to Gnome? if i'm even asking the correct question here Lol. XFCE all have the same themes, when GNOME has much better themes that i want to install but my system won't let me. maybe i'm doing it wrong, i don't know. 

Please reply :) Thank you in advance.

Xubuntu, Kubuntu, and all the variants are just Ubuntu with a different desktop environment, so any program for Ubuntu will work for Xubuntu, and visa versa.

---

### Post by davec64 on 2009-02-26
Silly question but you changed directory in the terminal to your desktop first?

```
cd Desktop
```

---

### Post by linuxisevolution on 2009-02-26
> **Gamak said:**
> ty, i've been having a lot of trouble with themes and such. the tarball files that come with some, i can't get them to install! or other such files as .gz . when i open terminal and type in the code that i'm supposed to, it says that the files cannot be found! and i have them on my desktop! any help with that? 

having loads of trouble Lol. but i still love linux more than windows Lol.
Make sure that you download the .tar.gz file and do not extract it.
If you talking about a regular Gnome theme, just right click the desktop, click Change Desktop background, Click Theme, and click Install.

---

### Post by Gamak on 2009-02-26
nope....Lol. i'm totally new to linux sorry for seeming so stupid, i am just super new Lol. so cd desktop will change the directory to desktop, and then the files that are on desktop can be installed through terminal? the ones that won't anyway. such as...

sudo cp -i file name usr/share/themes i think was the code that i was using.

---

### Post by stim on 2009-02-26
You can install both Gnome (which comes with Ubuntu by default) and XFCE.  I have Gnome XFCE and KDE all installed on my system right now.  The sessions menu from the login screen will allow you to choose which window desktop environment you would like  to use.  Open the package manager and install 'xubuntu-desktop' or alternatively you can 

```
sudo apt-get install xubuntu-desktop
```

---

### Post by Gamak on 2009-02-26
so for the .tar and .gz files, when i code sudo apt-get install xubuntu-desktop, it will allow me to install them? and the directory will be set to desktop then?

---

### Post by Snow Keld on 2009-02-26
in ubuntu (gnome) you can get the themes, best from gnome-look.org i think is the page, then you use the theme picker thing, same as to edit your desktop background and that stuff, it will install the theme for you from the tar.gz file.

and for testing other desktops like xfce or kde you can do it with the synaptic package manager rather than the terminal if you want (what i do, i'm useless with the command line)


i use xubuntu now cuz not all kde apps where working 100% on gnome, idk why, but xfce handles it all quite well, i have a pretty fast comp (640mb RAM + graphics card... thats not working atm :( )
its usefull to have your desktop run faster, it means you have more power to run more apps at a time :P


after you get the xubuntu-desktop or kubuntu-desktop from terminal or package manager you just choose the session type from the login menu.

---

### Post by Gamak on 2009-02-26
This is so hard once u learn to many things at once hahaha. now i donno what to do. this is the theme i want to install on xubuntu Lol. [http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619](http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619) it's BAD ***. can someone please tell me steps as to how to install that! Please and thanks :)! yes i'm a noob, hopefully someone on here can make me not a noob Lol.

---

### Post by Gamak on 2009-02-26
this theme is really pissing me off. Lol. i tried to install it into the usr/share/themes folder, but it DOESN'T work. it WON'T work for me, i don't know why, there is a readme file in that theme but it doesn't help at all, the file is a .tar.gz file, and i honestly don't have a clue what to do. can someone please tell me what to do, i am on a brand new xubuntu, do i need to set something up, or anything like that. someone please help me. :(

---

### Post by HuaiDan on 2009-02-26
Ok, take a deep breath.


First off, it should be
cd Desktop

not cd desktop

Bash is very case sensitive.

Also, when you extract or move the files to /usr/share, you either have to do it as su (recommended), or change the ownership of the /usr/share/themes folder.  Alternatively, you can drag and drop themes into the the appearance/themes window.

---

### Post by Gamak on 2009-02-26
"Also, when you extract or move the files to /usr/share, you either have to do it as su (recommended), or change the ownership of the /usr/share/themes folder."

The cd Desktop i figured out. and i got that fine. can u tell me the rest of the code that i need to extract that file? also, the themes that i put in the .themes folder that i had to create in home, only like...installs the colors to the top drop down menus, it physically doesn't change the looks. :S so thats why i want to learn how to do them the other way.

---

### Post by 4Orbs on 2009-02-26
The theme you linked to is an icon theme (icons only.. no gui theme). Is that what you intend to install? If so, then first extract the file to your desktop by double clicking (which will open your archive manager). Then click the extract button at the top of the archive manager, then click yes to extract the icon theme folder (to your desktop). Then open a terminal and enter
```
gksudo thunar
```
which will open your file manager as root user. Then navigate the file mgr to your desktop, copy the icon folder. Then navigate to your filesystem /usr/share/icons folder and paste the icon folder inside. You should then be able to select the new icon theme from Settings Mgr->User Interface button->Icons tab

---

### Post by Gamak on 2009-02-26
FINALLY SOMETHING WORKED hahahha. do u know what he is using to change his like...desktop arrangment what ever that is called? GUI? where it doesn't look like stock xubuntu. Lol. with the bar at top etc. thnx 4orbs :)

---

### Post by 4Orbs on 2009-02-27
In the comments on the theme page at gnome-look.org someone mentions the theme is Slickness, but I don't know for sure. Since you are using xubuntu, you should go to this website [xfce-look.org]("http://www.xfce-look.org") and choose your themes and icons there, because they are modified to work with xfce (xubuntu). Select the option in the menu on the website for gtk-2 themes. Then download them and install them the same way I described for the icon theme, but paste the theme folder into your /usr/share/themes folder. You might try the theme Overglossed orange, it is shiny and dark... pretty cool. It would probably look nice with the icons you installed earlier.

The theme won't change the number of panels (taskbars) on your desktop, it will change the color. If you want just one panel at the bottom, you change that by right-clicking on the panel and select "Customize Panel". Then you can delete the bottom bar, then move the top bar to the bottom and add the "Task List", "Trash Icon", "Workspace Selector" and any other widgets you might like (to add them, right click on the panel and select "Add New Item" which will bring up the master widget menu.

Some of the themes require a different theme engine to work correctly. They won't look good with the standard engine that comes with xubuntu. Other themes might require Emerald theme manager to look like the screenshots. So pay attention to all the information on the theme's home page.

---

### Post by Snow Keld on 2009-02-27
on my last install of xubuntu i went through the trouble of putting the themes in usr/share/

but you dont need to go through the hassle, go to your account directory (what would be home, has your username) and view + show hidden files

there should be 2 folders (among others) called .icons and .themes
you want to extract your GTK and xfce themes there (GTK theme for everything but your window decorations and xfce theme for window decorations) into the .themes folder and your icon theme that you posted up there into the .icons folder.

i think this will only add the themes to your own account, so it wont show up as a theme option for other accounts on the same install, but its not like that really matters much, it works and is very simple :D



hmm... this is assuming its 8.10 i never looked for theme folders on my 8.04 install as i had no idea it was possible, everyone told me what these guys said, put them in /usr/share/themes/  and  /usr/share/icons/
so i'm not sure if this works on 8.04 or not, never done it.

---

### Post by Gamak on 2009-02-27
thnx 4orbs, that helps a lot haha. i just kept getting pissed when i'd get a theme installed and then it wouldn't look like what i wanted hahahaa. i'd get so mad. i'll try that in a little bit, off to school now just got up. thnx again!

---

### Post by Gamak on 2009-02-27
hey 4orbs i tried the theme u suggested and it's super nice. :) works fine. ty ty! i love that theme. and the panels i done what u said and that looks a lot better. :) so ty again for your help, and everyone else that replied.

---

### Post by Snow Keld on 2009-02-27
ya, at xfce-look.org

i use themes...

carbon gold GTK 2.x
Ater Grey Alpha xfce (window decoration)
black-red icon theme off gnome-look.org

the icons are vista-like, but are a glossy dark red, the theme is dark, blacks and gray with gold font, and the window decoration matches with the gray, black and red.

---


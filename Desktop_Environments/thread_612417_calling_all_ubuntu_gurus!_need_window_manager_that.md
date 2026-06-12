---
title: "calling all ubuntu gurus! need window manager that works well with my gnome setup"
date: 2007-11-13
forum: Desktop Environments
---

### Post by LinuxSoundMan on 2007-11-13
i am a musician and i need a streamlined environment that doesnt eat up my resources. at the same time i need it to be user friendly because i am not an expert when it comes to text based commands. i have been experimenting with some different window managers but it seems like they dont integrate well with my existing gnome configuration. sometimes taskbar icons are missing and with openbox everything is missing and all i have is a right click menu. perhaps i should use a different environment? please help me i am desperately trying to create a streamlined cpu/user friendly ubuntu studio environment for audio and video production. thanks a lot. much appreciated.

---

### Post by climatewarrior on 2007-11-13
Maybe you should try the XFCE desktop environment. It is supposed to be really fast. You can try it out on your current ubuntu without losing anything and if you dont like it ou can remove it quite easily.

---

### Post by LinuxSoundMan on 2007-11-13
> **climatewarrior said:**
> Maybe you should try the XFCE desktop environment. It is supposed to be really fast. You can try it out on your current ubuntu without losing anything and if you dont like it ou can remove it quite easily.

that definitely seems like my best bet so far. ive tried the window manager and it seems like it would be good and stable. the only problem is i like the gnome panel items and i dont know if xfce has the same functions. thanks for the reply

---

### Post by LinuxSoundMan on 2007-11-14
which is the fastest most stable and functional desktop environment besides xfce. xfce is nice but i want to see what my options are. any advice would be good.thanks

---

### Post by LinuxSoundMan on 2007-11-14
also if i do decide to use xfce. how do i install the entire environment not just the win manager.?

---

### Post by PaganHippie on 2007-11-14
open a terminal window, and type:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xubuntu-desktop
```Either log out or reboot, and select Xfce from the session manager.  Then, go in to Synaptic and remove any apps that you don't want.  To save disk space and some system resources, you may also want to remove anything Gnome-related.  Fortunately, Synaptic sorts these out for you.

Xfce has some of the same panel items available as Gnome, or at least similar items, but not all of them.  I'm not sure what would happen if you tried to install Gnome panel items in Xfce, apart from increasing the system overhead by adding Gnome libs to a desktop that doesn't normally need them.  Might be fine, but then again....

Hope this helps.  I'm running Ubuntu (Gnome) on 2 systems and Xubuntu on 2 others currently.  Xfce is definitely much lighter than Gnome, but I'm also interested in hearing about other lightweight window managers.  A couple of years ago, icewm was very popular, but it doesn't seem to be the flavour of the month anymore....

---

### Post by LinuxSoundMan on 2007-11-14
thanks a lot for your post pagan. i seem to have gotten my head around xfce. it really is lighter and faster. and here is a quote directly from the xfce website. > Most of the additional panel plugins, available via the Xfce Goodies Project, have been updated for the new panel, and several new plugins were added. For example, the brand new xfce4-xfapplet-plugin allows users to add GNOME panel applets to the Xfce panel.  awesome. looks like i will be using xfce for now. thanks again to you pagan and all the gurus who help us noobs on this forum. the community support effort is a huge part of what separates linux/ubuntu from other OSs. thanks again.

---

### Post by TeaSwigger on 2007-11-14
> **LinuxSoundMan said:**
> thanks a lot for your post pagan. i seem to have gotten my head around xfce. it really is lighter and faster. and here is a quote directly from the xfce website.   awesome. looks like i will be using xfce for now. thanks again to you pagan and all the gurus who help us noobs on this forum. the community support effort is a huge part of what separates linux/ubuntu from other OSs. thanks again.

Please note: Xubuntu is not much lighter in resource use. To get a substantially lighter environment while still enjoying easy access to ubuntu's advantages, you may have to try the more esoteric Fluxbuntu - requiring a fresh install at this time - and probably take more time to get lighter versions of certain features. That's not to slight Fluxbuntu; I've tried it and find it to be beautiful and if you're particular what you install, noticeably lighter than Xubuntu. 

Further, I regularly use Fluxbox - Fluxbuntu's window manager - installed on top of Kubuntu, which tends to free around ~30mb ram on my particular setup while still using ubuntu/kubuntu apps. It is highly configurable and easy to use once one gets their head around it, being as it's customizeable mostly by simply editing some text files. 

Some things you can do to save some ram include:

-go with a really light distro like PuppyLinux.
-using ubuntu but running a lighter window manager than ubuntu's Gnome, kubuntu's KDE or xubuntu's xfce on it, such as IceWM or the aforementioned Fluxbox.
-using carefully chosen light apps in ubuntus, like pcmanfm for a file manager.
-of course not using eye candy like transparencies etc.

If you need any help in that way, ask and ask here as there are a number of folks who really know their way around this stuff.

---

### Post by LinuxSoundMan on 2007-11-14
thank you very much for your post TeaSwigger. I have taken a look at fluxbox and i even installed the manager on my ubuntu studio install and although it looks nice i cant seem to get a menu or anything which gives me acccess to my system. im sure this is a issue of my own ignorance to the operation of fluxbox. my main problem though is i use the Ubuntu Studio installation which supposedly is tailormade for audio/video production. if i were to go ahead and install fluxbuntu would i then essentially have to install each studio component by hand? such as the jack server, ALSA components, etc. I need it to be "audio ready". this could  turn out to be a very tedious process. but im sure its possible. thanks again for the advice.

---

### Post by LinuxSoundMan on 2007-11-14
i should also note that i absolutely need Wine and Wineasio functionality as i use a windows based digital audio software. thanks again.
Fluxbuntu looks absolutely amazing by the way. very minimal and thats exactly what ive been looking for. i had no idea. you really pointed me in the proper direction. one last note though. i have to say that i am a noob when it comes to command based operation. im guessing i will have to hit linuxcommand.org pretty hard to be able to use fluxbuntu.

---

### Post by TeaSwigger on 2007-11-14
Yes it could become a tedius process. All the more so because I haven't seen any listing of all of the packages that make up Ubuntu Studio or Fluxbuntu. There are lists for all the packages in the others. Fluxbuntu is too new, and both are rareities among the Ubuntus, making them real esoteric I guess. I'm sorry it's that way, I love music & multimedia too.

How badly do you need to save resources though if I may ask? Is Ubuntu Studio performing too slowly on the unit? It's kind of hard to suggest what may entail a lot of initial time if not.

About Fluxbox, yeah the menu's typically pretty darn thin by deafult. You can change the menu or even make it yourself; here is a thread that has tons of info about Fluxbox:
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)
Regulars 'RedSquirrel' and 'yabbadabbadont' are among those you can find here that know the ins and outs real well if you do want to work with a Fluxbox on Ubuntu Studio route.

the Fluxbuntu project is independent of Ubuntu proper and is based here:
[http://www.fluxbuntu.org](http://www.fluxbuntu.org)
you can see some caps of their interesting default look. They have a forum which you might also find help at. While you're sure to have sound with some alsa support I don't know if it's set up with much you'd need for heavy production. You would have easy access to installing any missing ubuntu packages on it, but I've no idea if you'd be much ahead performance wise vs. Fluxbox on Ubuntu Studio after you were done.

Ubuntu and relatives are astonishing at making these super-complex sophisticated systems relatively easy in default forms but unfortunately it sure can get involved when you need to go customizing. 

ps in case you don't know yet, if you need to see ram / cpu use and what's using what, what you can do is open a terminal and just enter the word top. It gives a real time run-down. 

Again, good luck to ya and always feel free to ask anything.

---

### Post by LinuxSoundMan on 2007-11-14
your advice is very much appreciated. i will definitely be doing some reading today. it seems that there is a plethora of options not only within linux but even within ubuntu.> How badly do you need to save resources though if I may ask? Is Ubuntu Studio performing too slowly on the unit? It's kind of hard to suggest what may entail a lot of initial time if not. it actually performs quite well but i could definitely do away with the bells and whistles that clog up the cpu during heavy production.(using a lot of VST plugins, etc.) also since i use Wine in conjunction with WineASIO to run my main audio software i was under the impression that a more streamlined window manager would contribute to Wines performance when it came to GUI redrawing and the like. I would love to have the simplicity and minimal aspects of fluxbox combined with the user friendlyness of gnome or xfce. perhaps this is asking too much. thanks again for your posts. it helped a lot.

---

### Post by TeaSwigger on 2007-11-14
> **LinuxSoundMan said:**
> i should also note that i absolutely need Wine and Wineasio functionality as i use a windows based digital audio software. thanks again.
Fluxbuntu looks absolutely amazing by the way. very minimal and thats exactly what ive been looking for. i had no idea. you really pointed me in the proper direction. one last note though. i have to say that i am a noob when it comes to command based operation. im guessing i will have to hit linuxcommand.org pretty hard to be able to use fluxbuntu.

Guess we were posting at the same time :)

Ah ok. Yeah it's one interesting, attractive setup, Fluxbox and Fluxbuntu. Awesome style in my humble. :guitar:

WINE can be a beast of its own lol. Can be tricky. It's pulling off quite a feat though. If WINE just won't do by the way, you're not out of luck yet. There's virtualization which can run an actual Windows install inside Linux. Both WINE and virtualization will work in any of the ubuntu varieties, but virtualization method demands a lot of resources especially memory.

Well the commands, I don't know if you'd really need a lot more command line work in Fluxbuntu than Ubuntu Studio; perhaps not. More just figuring out Fluxbox, Fluxbuntu's very fast and nifty but quirky file manager ROX-Filer, and what stuff you need to install and the stuff specific to each. 

I should probably stress that the command line is powerful in linux and there are a whole lot of things one can do with it and with apps made to work in just the command terminal. Including a lot of media related things. There's nothing that works faster and takes less resources than working in a command line environment. Not that I love working in it, heck I don't know all that much in it. But it could be invaluable to your work to become handy in that stuff. Whatever you do I hope you enjoy yourself :)

---

### Post by LinuxSoundMan on 2007-11-14
i run wine flawlessly in ubuntu studio so i would imagine it would work the same within fluxbuntu. i dont really care for the extra bells and wistles contained within the ubuntu studio release because the heart of my production is done within a windows based program. that is why wine is so essential. my main concern is being able to install the necessary packages to ensure that i can run my windows based audio program and wineasio which is a low latency driver for your sound card which also requires the jack server to function properly. other than that i can do away with the rest of ubuntu studio minus a few software packages for syntheses etc which im sure could be acquired with the awesome and painless apt-get command because all the software in ubuntu studio is available in the repositories. so i guess my question is this. do the ubuntu studio or ubuntu proper for that matter integrate with fluxbuntu. > Well the commands, I don't know if you'd really need a lot more command line work in Fluxbuntu than Ubuntu Studio; perhaps not. More just figuring out Fluxbox, Fluxbuntu's very fast and nifty but quirky file manager ROX-Filer, and what stuff you need to install and the stuff specific to each. that is definitely good to know. im starting to look at fluxbuntu more and more. > While you're sure to have sound with some alsa support I don't know if it's set up with much you'd need for heavy production. You would have easy access to installing any missing ubuntu packages on it, but I've no idea if you'd be much ahead performance wise vs. Fluxbox on Ubuntu Studio after you were done. i guess going this route would do away with any "bloat" which is essential to me. i love the ubuntu studio release but like i said theres a lot of software included that i would never use. so streamlining is my main concern as well as finding slick and fast window management. thanks again. BTW, the "top" command is extremely useful thanks for that.

---

### Post by urukrama on 2007-11-14
> **LinuxSoundMan said:**
>  with openbox everything is missing and all i have is a right click menu.

That is indeed all that Openbox offers, but rather than seeing it as deficient because of that, I think it is Openbox's greatest strenght. Editing the menu is very easy if you use obmenu, and if you want a panel, you can add one (fbpanel, lxpanel, pypanel, gnome-panel, xfce4-panel, etc.). If you want light, configurable, and aesthetically pleasing, Openbox is the way to go. It will requiire some time to set it up and perhaps to get used to it, but it is the perfect environment if you want to be productive and efficient without wobbly windows or fancy effects.

If you need help with setting Openbox up, there are a few guides on these forums (search for 'Openbox' and 'howto')

Xfce is pretty decent too, though I find Xubuntu slow. Instead of installing xubuntu-desktop, try installing xfce4:

```
sudo aptitude install xfce4
``` 

You get the same desktop environment, but without all the extra packages that xubuntu carry with it.

---

### Post by LinuxSoundMan on 2007-11-14
i see what youre saying about openbox. indeed very light. i will look into this as well. it looks like i will either be using flux or open box systems. thanks for the post

---

### Post by LinuxSoundMan on 2007-11-14
any info on how to get a menu of my installed aps in fluxbox. all i get is a blank screen. i accidentally made the bar at the bottom invisible and now i have nothing but a blue screen, i know im doing something horridly wrong, once again excuse my noobness here.

---

### Post by LinuxSoundMan on 2007-11-14
ok i managed to get a panel up in openbox but everytime i close terminal the panel disappears. any info on this would help.

---

### Post by urukrama on 2007-11-14
> **LinuxSoundMan said:**
> ok i managed to get a panel up in openbox but everytime i close terminal the panel disappears. any info on this would help.

You'll have to add it to your autostart file (more info [here]("http://icculus.org/openbox/index.php/Help:Autostart")) Add a line like this:

> *nameofthepanel &*

Make sure the & is at the end, as it indicates that more things need to be loaded; if you leave it out Openbox won't start.

If you don't want the panel to start whenever you start Openbox, you can use gmrun (in the repos) and bind it to a keyboard shortcut (Alt+F2 for me) in the rc.xml file. Add this to the keyboard section in that file:

```
<keybind key="A-F2">
      <action name="execute">
        <execute>gmrun</execute>
      </action>
    </keybind>
```

For help with Fluxbox menus, have a look [here]("http://ubuntuforums.org/showthread.php?t=371144").

---


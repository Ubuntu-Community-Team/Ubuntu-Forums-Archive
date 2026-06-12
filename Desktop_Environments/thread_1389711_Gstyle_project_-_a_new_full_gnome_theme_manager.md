---
title: "Gstyle project - a new full gnome theme manager"
date: 2010-01-24
forum: Desktop Environments
---

### Post by smo on 2010-01-24
hello

i make a post there to get a small feedback on our small project, gstyle

this software try to concentrate every possibles themes types in one main window with easy install of new themes form gnome-look, deviantart, customize.org... or by direct download from the software ;)

here s a video to show you:
[http://www.penguincape.org/downloads/gstyle/videos/gstyle-preview.ogv](http://www.penguincape.org/downloads/gstyle/videos/gstyle-preview.ogv)

to install from ppa:

```

sudo apt-add-repository ppa:s-lagui
sudo apt-get update
sudo apt-get install gstyle


```

if you find some strange traduction (we re french) or want to help, let us know ;)

thanks

++

---

### Post by smo on 2010-01-25
ola

anybody s interested !! ??? ;)

---

### Post by cybergalvez on 2010-01-26
well I was hopping to see what others were going to say before I tried it, but since noone seems to be doing that I will take the plunge because the vids look fantastic and will post my results after I've given it a try

---

### Post by cybergalvez on 2010-01-26
> **smo said:**
> ola

anybody s interested !! ??? ;)

tried to install and got this error:
raceback (most recent call last):
  File "gstyle.py", line 43, in <module>
    Gstyle()
  File "gstyle.py", line 18, in __init__
    config.check_config()
  File "/home/jjgalvez/gstyle/config.py", line 58, in check_config
    os.mkdir(emerald_home_srcdir, 0755)
OSError: [Errno 2] No such file or directory: '/home/jjgalvez/.emerald/themes'

---

### Post by cybergalvez on 2010-01-26
ok created the .emerald/themes folder and that fixed that. first look it loosk pretty cool, I will write a better review soon

---

### Post by nilarimogard on 2010-01-27
Wow, it looks awasome. I just run it for the first time and everything seems to be working fine for now!

---

### Post by smo on 2010-01-27
hello

thanks :)

i fixed your small bug yesterday cybergalvez, we ll continue the dev this week end i think (too much work on it last week...)

Do not hesitate to post your requests or bug ;)

hummm, english traduction is right ?

++

---

### Post by nilarimogard on 2010-01-28
I made a post about your application, I hope you don't mind I uploaded your video to YouTube...

The post is called [Try Gstyle Project, A New Gnome Theme Manager]("http://www.webupd8.org/2010/01/try-gstyle-project-new-gnome-theme.html")

I have a question: I saw your application suggests using a script called cfinstall.sh to install the latest Compiz from GIT. Is there any chance you can translate it into English? That would make things a lot easier for people wanting to try this out.

---

### Post by chaopoch on 2010-01-28
As you can see in the screenshot attached, I have installed and enabled the cubemodel plugin, but when I run command 'python gstyle.py', it still shows the following error message that no Default.ini file found in directory  /home/paulchang/.config/compiz/compizconfig, any comment?

.....
[COLOR="SeaGreen"]Traceback (most recent call last):
  File "gstyle.py", line 43, in <module>
    Gstyle()
  File "gstyle.py", line 38, in __init__
    self.gtk_gui = MainWindow(self)
  File "/home/paulchang/gstyle/gui/main.py", line 51, in __init__
    self.cubemodel_obj = CubemodelsGui(self.wTree,gstyle_obj.cubemodels_dict)
  File "/home/paulchang/gstyle/gui/cubemodels.py", line 104, in __init__
    self.check_conf()
  File "/home/paulchang/gstyle/gui/cubemodels.py", line 274, in check_conf
    self.cubemodels_dict.check_plugins()
  File "/home/paulchang/gstyle/lib/cubemodels.py", line 88, in check_plugins
    compiz_ini.readfp(open(compiz_config))[/COLOR]
[COLOR="Red"]IOError: [Errno 2] &#27794;&#26377;&#27492;&#19968;&#27284;&#26696;&#25110;&#30446;&#37636;: '/home/paulchang/.config/compiz/compizconfig/Default.ini'[/COLOR]


[ATTACH]145211[/ATTACH]

---

### Post by smo on 2010-01-28
ola

thx a lot nilarimogard, cool to see our soft on webup8.org ;) very nice and clear post ;) np for the video on youtube...

maybe you can add that this svn version often need update

cd /thegstyle/dir
svn update

... ;)


About gstyle, (i ll try to be clear :)) 

filtres have been corrected for each file-select dialogs, fullpacks is now 90% working but we still have some work on wallpapers/walldyn and translations (and some other details...)

For the compiz script and the cubemodel's "problem" (i will see for english traduction)

I removed the cubethemer option (integrated in gstyle)

and replaced it by a "cubemodel" option, this function just dowload and install a .deb file of the cubemodel plugin builded with checkinstall (not clean but right for a so small package)

the package is available here (so you don t need the script anymore):
[http://www.ubukey.fr/custom/deb/karmic/cubemodel_20100129-1_i386.deb]("http://www.ubukey.fr/custom/deb/karmic/cubemodel_20100129-1_i386.deb")

it need some tests but since git and karmic repositories have the same compiz version, normaly it must work for everybody, you can install the full compiz too if you want/need ;)

once the gstyle deb file is done we'll add this cubemodel deb as dependencies i think (if it works...)

chaopoch:

if you used our script, launch it, check the "Config" option then restart compiz by fusion-icon or restart your session 

good luck


thx all

++

---

### Post by BoredOutOfMyMind on 2010-01-28
I get a few errors and since I do not speak French, I am uncertain if there are a few more. 

Seems to hang here after asking to install the cubemodels. 

> ./configure: line 4215: intltool-update: command not found
configure: error: Your intltool is too old.  You need intltool 0.23 or later.

rm: cannot remove `/opt/cfinstall/compiz-build/Master/compiz': No such file or directory

 #########################################################
 
 Une erreur a été rencontrée pendant l'opération :
 Autogen de compiz Merci de copier/coller les lignes ci dessus entre les #
 sur le forum ubuntu ^^
 
Sortie...


Ajouts des elements d autostart Pour votre session compiz-fusion... 

Téléchargement du plugin cubemodel...
Démarre de l'installation/mise à jour du plugin cubemodel...


I will install intltool and see if this works the second time around.....

---

### Post by smo on 2010-01-28
hi

yeah that s what you need but cubemodel option alone is ok if you only want to test gstyle (and have compiz working...)

++

---

### Post by chaopoch on 2010-01-28
> **smo said:**
> ...
chaopoch:

if you used our script, launch it, check the "Config" option then restart compiz by fusion-icon or restart your session 

good luck
...


I did not install Compiz from git, so I **CAN NOT** use your script to install cubemodel, this plugin was compiled and installed from source.

I restart the session, but the problem persists, any more solution?

Thanks.

---

### Post by BoredOutOfMyMind on 2010-01-28
> **smo said:**
> hi

yeah that s what you need but cubemodel option alone is ok if you only want to test gstyle (and have compiz working...)

++

maybe an icon installed in Applications> System Tools would be nice also....:D

So far looks real good after the second round of install. 

Now to try XSplash!

:D

---

### Post by chaopoch on 2010-01-29
> **chaopoch said:**
> I did not install Compiz from git, so I **CAN NOT** use your script to install cubemodel, this plugin was compiled and installed from source.

I restart the session, but the problem persists, any more solution?

Thanks.

I solve the problem by creating a empty Default.ini in ~/.config/compiz/compizconfig/

---

### Post by chaopoch on 2010-01-29
I create a deb to install and to update Gstyle more easily for newbie, this package includes launchers for opening/updating Gstyle, you can find them in **Applications -> Other**, the cubemodel plugin for Compiz 0.8.2 is also included.

You can download gstyle-0.1_i386.deb from here:
[http://www.adrive.com/public/e2f6ea75577230289debfe69d562c2989fe8d3eff5b9f3e10afe1ce732059450.html](http://www.adrive.com/public/e2f6ea75577230289debfe69d562c2989fe8d3eff5b9f3e10afe1ce732059450.html)

however, there are two problems still need be solved.

1. You have to create a empty **Default.ini** in ~/.config/compiz/compizconfig/

2. I can download cubemodel themes, but still don't know how to enable the effect.


[ATTACH]145379[/ATTACH]

---

### Post by smo on 2010-01-30
ola

thanks chaopoch for the deb, i ll try it very soon

for your problem, do you have compiz ok and running ?

since the Default.ini is one of the first files created by compiz (not gstyle related) it s very starnge that you don t have it, or not edited since you created an empty file for it....

we ll add a check for compiz 

++

---

### Post by chaopoch on 2010-01-30
> **smo said:**
> ...
thanks chaopoch for the deb, i ll try it very soon..

I like Gstyle very much, and hope to do something for it, I am not a progammer, so this deb is the only thing that I can do.

PS: I just uploaded a bug-fixed deb 30 minutes ago.

> **smo said:**
> ...
for your problem, do you have compiz ok and running ?...

I have been using Compiz for quite a long time, and it works just great.

I installed many plugins from sources before, this is the first time that I install cubemodel and don't know how to use it.

> **smo said:**
> ...
since the Default.ini is one of the first files created by compiz (not gstyle related) it s very starnge that you don t have it, or not edited since you created an empty file for it...

I don't know why Default.ini did not come with Compiz? and I did just add a empty Default.ini to fix the problem I ever described, I also think it is weird.

---

### Post by smo on 2010-01-30
yes very strange :)

so what do you have now in this Default.ini ?

and everything works (for compiz) but cubemodel? 

if it s the case, maybe the plugin path is not the same between the deb i made for cubemodel and the compiz deb you used from repositories

i install the plugin in /usr/local and ubuntu debs in /usr...(not sure)

Try (to see):

git clone git://anongit.compiz-fusion.org/fusion/plugins/cubemodel
cd cubemodel
make install


it will create a .compiz/plugins and metadata in your home, then reload compiz, we can t do better

---

### Post by smo on 2010-01-30
Walldyn and fullpacks now 100% ok !

we ll work on translations now and fix all small bugs...we try to integrate a walldyn creator too ;)

++

---

### Post by chaopoch on 2010-01-30
> **smo said:**
> yes very strange :)

so what do you have now in this Default.ini ?...

[[COLOR="Green"]cube]
s0_skydome_animated = true
s0_color = #00000000
s0_scale_image = true
as_next_slide_key = Disabled
s0_skydome_image = /home/paulchang/.config/gstyle/elements/cubemodel/Rattler/skydome//save-da-planet-01-2048x1024.png
s0_adjust_image = true
s0_active_opacity = 0.000000
s0_skydome = true

[cubemodel]
s0_concurrent_load = false
s0_model_x_offset = 0.000000;
s0_model_animation = 1;
s0_model_rotation_rate = 0.000000;
s0_model_filename = /home/paulchang/.config/gstyle/elements/cubemodel/Rattler/obj/Rattler/Rattler_0.obj;
s0_global_model_scale_factor = 6.707200
s0_model_scale_factor = 0.710000;
s0_model_fps = 7;
s0_light_diffuse = 0.821800
s0_model_z_offset = -1.000000;
s0_render_front_and_back = true
s0_light_specular = 1.000000
s0_model_rotation_plane = 0;
s0_model_y_offset = 0.000000;
s0_light_ambient = 0.992600[/COLOR]

> **smo said:**
> ...
and everything works (for compiz) but cubemodel? 

if it s the case, maybe the plugin path is not the same between the deb i made for cubemodel and the compiz deb you used from repositories

i install the plugin in /usr/local and ubuntu debs in /usr...(not sure)
...

Yes, everything works for compiz except the cubemodel.

For the compiz installed from repository, all the .so plugin files are placed in /usr/lib/compiz and the .xml metadata files in /usr/share/compiz, and those are where I put the libcubemodel.so and cubemodel.xml in my deb. 

But, I find one thing strange, although these two files libcubemodel.so and cubemodel.xml are in the right directory respectively, I can not find the 'Cube 3D models' plugin in CCSM until I copy libcubemodel.so to ~/.compiz/plugins and cubemodel.xml to ~/.compiz/metadata.



BTW, do I have to set up anything in CCSM after I install cubemodel plugin to enable it?

---

### Post by smo on 2010-01-31
normally you must see 

/home/paulchang/.config/gstyle/elements/cubemodel/Rattler/obj/Rattler/Rattler_0.obj;

when you enter in cube 3D models, but the problem is not there i think

maybe you use gconf only to configure compiz

compizconfig-backend-gconf installed?   (if yes, try to remove it) and install fusion-icon if not installed


maybe another solution:

1/ create a file
/home/paulchang/.config/compiz/compizconfig/config

2/ put this in the file:

[gnome_session]
backend = ini
profile = 

3/remove the Default.ini

4/restart compiz

---

### Post by chaopoch on 2010-01-31
> **smo said:**
> ...maybe you use gconf only to configure compiz

compizconfig-backend-gconf installed?   (if yes, try to remove it) and install fusion-icon if not installed...

If I remove compizconfig-backend-gconf, all the following packages will be removed,

compiz, compiz-gnome, fusion-icon, gstyle

so I can not remove it.

> **smo said:**
> ...
maybe another solution:

1/ create a file
/home/paulchang/.config/compiz/compizconfig/config

2/ put this in the file:

[gnome_session]
backend = ini
profile = 

3/remove the Default.ini

4/restart compiz

1. The file config is already there, and the following lines are in it,

[COLOR="Blue"][gnome_session]
profile = 
plugin_list_autosort = true[/COLOR]

2. If I put the line **backend = ini** in file config, I will lose all the personal settings in CCSM, and the Sphere effect will be switched to Desktop Wall. 

I remove the line, and everything gets back.

3. I remove the Default.ini, but it is immediately created by itself just after I delete it, so I **can not** remove it.

---

### Post by smo on 2010-01-31
ola

so the question is where your actual config is stored?

and the deb is not a good thing :(

i ll test it all form a live-cd with "normal" compiz from repo to see if i have the same problems 


ps: i think you can export your config from ccsm, switch to ini backend then import your config maybe ?

++

---

### Post by smo on 2010-01-31
ok i m on a live-cd

so keys are right in gconf-editor (or xml files)

apps/compiz/plugins....

i search how to switch from gconf to ini backend without losing configuration...

compizconfig-settings-manager not available directly :(

++

---

### Post by smo on 2010-01-31
ok it works very well

in ccsm go to settings, export your config, and just select "flat-file" configuration backend in the backend section, now import your config file

it create the Default.ini with all your settings

i try to install cubemodel and gstyle now

---

### Post by smo on 2010-01-31
ok

so 3 problems we ll have to fix first

.gnome2/backgrounds.xml is not created on a fresh install or live-cd until i start "gnome-apparence"

this Default.ini problem, i ll find howto export gconf config with gconftool-2 i think...

and the deb i made is bad, not working in ccsm, we ll have to find another solution as we can t use homedir as install dir in a deb i think ??

---

### Post by chaopoch on 2010-01-31
> **smo said:**
> ok i m on a live-cd

so keys are right in gconf-editor (or xml files)

apps/compiz/plugins....




I find **NO** cubemodel key in apps/compiz/plugins, why?

---

### Post by smo on 2010-02-01
ola

no way to export the gcong config as a flat file for me :(

did you tried :

git clone git://anongit.compiz-fusion.org/fusion/plugins/cubemodel
cd cubemodel
make install

then verify if you have the key (i have it)

?

---

### Post by chaopoch on 2010-02-01
> **smo said:**
> ola

no way to export the gcong config as a flat file for me :(

did you tried :

git clone git://anongit.compiz-fusion.org/fusion/plugins/cubemodel
cd cubemodel
make install

then verify if you have the key (i have it)

?

Unfortunately, there is still **NO** key, I just don't understand why could this happen?

---

### Post by chaopoch on 2010-02-01
I manually create a empty folder cubemodel in ~/.gconf/app/compiz/plugins, and add a new model snowman.obj in CCSM->Cube 3D models->General from the package downloaded from git, well it works, here is the screenshot,

[ATTACH]145686[/ATTACH]

but it won't work when I select and activate a theme from Gstype,

[ATTACH]145688[/ATTACH]
[ATTACH]145687[/ATTACH]

then I add an obj file of the theme downloaded from Gstype, it shows the image, of course, only a component of the complete theme.

[ATTACH]145690[/ATTACH]
[ATTACH]145689[/ATTACH]


so, the problem needs to be solved is why the theme downloaded from Gstyle does not work?

---

### Post by chaopoch on 2010-02-03
> **chaopoch said:**
> ...
so, the problem needs to be solved is why the theme downloaded from Gstyle does not work?

Any comment about this question?

Cubemodel effect is the only problem of Gstyle on my computer now, I am still looking for solution for it, thanks.

---

### Post by smo on 2010-02-04
ola chaopoch

we re working on this problem, i think we have 1 or 2 solutions i need to test before ;)

i let you know when it s done

try this please:

gconf-schemas --register  /where/is/the.schemas of the cubemodel

and you might have the key in place ;)

it s the command used in the postinst of compiz-extras .deb so normally must work... if it s ok we just have to add it in my deb or yours in the postinst file

++

---

### Post by chaopoch on 2010-02-04
> **smo said:**
> ola chaopoch

we re working on this problem, i think we have 1 or 2 solutions i need to test before ;)

i let you know when it s done

try this please:

gconf-schemas --register  /where/is/the.schemas of the cubemodel

and you might have the key in place ;)

it s the command used in the postinst of compiz-extras .deb so normally must work... if it s ok we just have to add it in my deb or yours in the postinst file

++

I compiled and installed cubemodel from source, so I register the schema with this command, and reboot the computer:

$ sudo gconf-schemas --register /home/paulchang/Compiz/cubemodel/build/compiz-cubemodel.schema

while returning to the desktop, I run the following command to check if the schema is loaded, but it is not, of course, no cubemodel effect activated.

$ ls -l `locate --regex 'compiz-.*.schema'`
-rw-r--r-- 1 paulchang paulchang   8656 2010-02-02 10:05 /home/paulchang/Compiz/cubemodel/build/[COLOR="red"]compiz-cubemodel[/COLOR].schema
-rw-r--r-- 1 paulchang paulchang  18763 2009-10-25 07:56 /home/paulchang/Compiz/freewins/build/[COLOR="red"]compiz-freewins[/COLOR].schema
-rw-r--r-- 1 paulchang paulchang  11963 2009-10-25 08:16 /home/paulchang/Compiz/stackswitch/build/[COLOR="red"]compiz-stackswitch[/COLOR].schema
-rw-r--r-- 1 paulchang paulchang  24697 2009-10-25 08:10 /home/paulchang/Compiz/wizard/build/[COLOR="red"]compiz-wizard[/COLOR].schema
-rw-r--r-- 1 root      root        5817 2009-10-23 05:50 /usr/share/gconf/schemas/compiz-3d.schemas
-rw-r--r-- 1 root      root        3043 2009-10-23 05:50 /usr/share/gconf/schemas/compiz-addhelper.schemas
-rw-r--r-- 1 root      root       19940 2009-10-23 05:50 /usr/share/gconf/schemas/compiz-animationaddon.schemas
-rw-r--r-- 1 root      root       32065 2009-10-16 03:39 /usr/share/gconf/schemas/compiz-animation.schemas
-rw-r--r-- 1 root      root       40791 2009-12-03 16:28 /usr/share/gconf/schemas/compiz-annotate.schemas
-rw-r--r-- 1 root      root        3355 2009-10-23 05:50 /usr/share/gconf/schemas/compiz-bench.schemas
-rw-r--r-- 1 root      root          75 2009-10-23 05:50 /usr/share/gconf/schemas/compiz-bicubic.schemas
-rw-r--r-- 1 root      root       70802 2009-12-03 16:28 /usr/share/gconf/schemas/compiz-blur.schemas
-rw-r--r-- 1 root      root        4741 2009-12-03 16:28 /usr/share/gconf/schemas/compiz-clone.schemas
-rw-r--r-- 1 root      root        4010 2009-10-16 03:39 /usr/share/gconf/schemas/compiz-colorfilter.schemas
-rw-r--r-- 1 root      root      269573 2009-12-03 16:28 /usr/share/gconf/schemas/compiz-commands.schemas
-rw-r--r-- 1 root      root      303354 2009-12-03 16:28 /usr/share/gconf/schemas/compiz-core.schemas
-rw-r--r-- 1 root      root        2042 2009-10-23 05:50 /usr/share/gconf/schemas/compiz-crashhandler.schemas
-rw-r--r-- 1 root      root       17704 2009-10-23 05:50 /usr/share/gconf/schemas/[COLOR="Red"]compiz-cubeaddon[/COLOR].schemas
-rw-r--r-- 1 root      root      128581 2009-12-03 16:28 /usr/share/gconf/schemas/[COLOR="red"]compiz-cube[/COLOR].schemas
-rw-r--r-- 1 root      root          75 2009-12-03 16:28 /usr/share/gconf/schemas/compiz-dbus.schemas
-rw-r--r-- 1 root      root       47009 2009-12-03 16:28 /usr/share/gconf/schemas/compiz-decoration.schemas
...

As you can see, I had installed from sources the other three plugins, freewins, stackswitch and wizard, and their corresponding schema compiz-freewins.schema, compiz-stackswitch.schema
and compiz-wizard.schema are not under /usr/share/gconf/schemas/ either, but they just work after installation, I just don't understand why cubemodel does not work with the same way of installation?

---

### Post by Flimm on 2010-02-13
Hello smo!

I'm the developer of [Epidermis](http://epidermis.tuxfamily.org), a theme manager for GNOME. I guess that makes us competitors!

I've tried your program and I quite like it, although I have to say we have a quite different approach to it. Gstyle tries to create an extended appearance configuration utitility, while Epidermis tries to bring package management to themes.

It would be great if we could combine efforts. We already use the same programming language. On pourrait communiquer en Français si vous voulez. And we both want to make theming on Linux awesome!

For those who want a quick summary of the differences between Gstyle and Epidermis:

Gstyle's unique features:
[list][*] Compiz cubemodels are supported. You can download and install them automatically.
[*] Greater configurability: you can configure Xsplash yourself, instead of just installing Xsplash themes.
[*] Emerald themes are supported.[/list]

Epidermis' unique features:
[list][*] You can make your own collections of themes (skins) easily.
[*] Splash screens for GNOME, GRUB (1) themes and GDM themes are supported.
[*] Has own mime-type called pigment. Double click on .pigment file to open and install it with Epidermis. .pigment files are automatically thumbnailed in your file browser.[/list]

Right now I'm designing a specification for [universal themes](http://epidermis.tuxfamily.org/blogs/flimm/10/02/04/universal-themes-an-idea). I would love your feedback on this.

EDIT: I just found out that you contributed to Epidermis by translating it into French! Thanks for that.

---

### Post by smo on 2010-02-15
hello flimm

i follow epidermis since the beginning of your project and made the french translation as you see it ;)

my "problem" was with the pigment system, i needed something still using tar.gz or other files from the differents themes websites like gnome-look deviantart etc... and learn python too, that s why we created gstyle

i ll be happy if we can collaborate!

we still have to create our theme creator like yours (great)

for the moment i m in battle with those damn cubemodel plugin :D

for chaopoch i made an email to cubemodel's dev, here s the answer
(great)


Hello,

Nice to see my cubemodel plugin is being used elsewhere.

I remember having a lot of fun writing the plugin. However, I haven't done any work on compiz plugins for over a year now and haven't tried it with an up to date version of compiz.

I will be happy to port it over to 0.9 and see about make a deb compatible with Ubuntu (I'm running 9.10) -- maybe sometime over this week. This will be a good opportunity to see what is new in compiz development for me.
Thanks for the e-mail.

David


so i think we ll have a deb specially for karmic very soon and a rewrited version for next compiz version (0.9) wich is in a good way now !!


Zgegball, the bisigi project themes's creator joined us too ;)

flimm you can join us on jabber, my jabber is [email]smo@jabber.fr[/email]
and we have a "tchat" 

ubu-personnalisation on chat.jabberfr.org


Edit: i like your utheme idear, i personnaly tried to speak gnome's dev about it, they were not really interested... :(

and it don t seems to take a better way with gnome3...

++

---

### Post by smo on 2010-02-17
Ola

flimm you tried to join me yesterday but i m not at home before 11.30 pm...

So makes mail or call me in the night ;)

++

---

### Post by shrimpy89 on 2010-02-23
This looks like a fantastic idea.  I'm particularly interested in the Cubemodels.  Never seen anything like that before.  But when I click "Refresh" in the Download tab, the window goes gray and the connection eventually times out.  I'm not sure if this is a bug or I installed it wrong (I don't speak much French).  As for the rest of it, please keep up the good work!

---

### Post by hariks0 on 2010-02-26
Hi smo, Thank you first for such a good program and compiz script.=D> But as you see, your work has been appreciated and accepted by many of us and there rises the requirement of a globalised version of your script. Many problems could have been solved without disturbing you had the script and its output been in English.

For me, the script did almost all plugin install but some were missing from the CCSM. Newton physics, stackswitcher were some of them. There has been error messages related to these. But I could not understand them. They seemed to be some issued regarding some folders. I will try again and repost the exact messages I got.

BTW, is GStyle a separate project than the compiz script? Should I install both or what? lso tell me whether the ccsm is the latest one or not. I thought the previous ccsm about box was dated upto 2009. But the one after this script displays only 2008.

Thank you for your good work\\:D/

---

### Post by smo on 2010-02-28
hello

thanks for the reply

so, i know we have some "problems" with the cubemodel dependencies
we can t find a good solution for the moment for peoples with compiz installed from ubuntu repo and those with git version (wich is the same...)
but i build all plugins on the compiz git, that s the only differencies finally, and the script is normally a completely separated project (my first script ever...)

if mail the cubemodel author and he ll first rewrite his plugin for the incoming compiz 0.9 version and make a deb (with gconf keys) for karmic really soon, so we ll wait

for the refresh problem in the download tabs, it s fixed... we had to change our 'host ?', that s why you had problems with compiz script and downlods pages in gstyle...

The fullpacks section have been updated and we now have the good base for theme editor/creator in the same time with preview of each elements in a fullpack ! all the bisigi project are included with nice preview image 

i still have some problems with the gtk theme preview (i checked your code for that flimm, we approximately had the same code) contact me if we can speak about that (i have good info from gtk+ dev) and maybe i can create some pigments too in my futur fullpack creator ? or we can speak about your universal theme systeme for it ....

i rewrited the First post, we moved the code to github, so remove your actual gstyle folder and your /home/xxx/.config gstyle folder before redownload it please ;)

you can donate to encourage us on :
[http://gtk-apps.org/content/donate.php?content=120111](http://gtk-apps.org/content/donate.php?content=120111)

please let your comments ;)

++

---

### Post by dichtbijzee on 2010-02-28
I'm liking the features of gstyle alot, especially the "full theme" support.
It is a bit slow starting up. Is this because there is no caching?
Also the wallpapers added in the wallpaper tab don't get added to the gdm/xsplash tab.

Oh and changing tabs while installing a full theme isnt a good idea.

---

### Post by smo on 2010-02-28
hi

yes for the moment we scan everything in the system when gstyle start...

we ll record it in a xml later...

- Also the wallpapers added in the wallpaper tab don't get added to the gdm/xsplash tab

Thansk, i ll fix it and add image preview like fullpack i think

- Oh and changing tabs while installing a full theme isnt a good idea. ??

could you explain ?



we are doing a walldyn creator too ;)

---

### Post by dichtbijzee on 2010-02-28
wow, :O you are fast man.

> Thansk, i ll fix it and add image preview like fullpack i think

That was my next question. nice! 

> - Oh and changing tabs while installing a full theme isnt a good idea. ??

could you explain ?

While I download a fulltheme, and change tabs the program just hangs until everything is downloaded.

One final pointer, maybe you could switch over to tabs instead of buttons on the left.

---

### Post by smo on 2010-02-28
;)

While I download a fulltheme, and change tabs the program just hangs until everything is downloaded.

i see, i have some problems with threads, don t really understand it so i keep it for the end when we ll clean the code... but at the end normally it ll not hang like that (like when downloading a theme)


One final pointer, maybe you could switch over to tabs instead of buttons on the left.

i note , but we ll see that later :D

thx

++

---

### Post by smo on 2010-02-28
ok, preview in xsplash works

i ll work on it again in the next days when i ll have found a solution for gtk preview...

i made a push on the git...

++

---

### Post by fallenshadow on 2010-02-28
wow this actually looks really awesome! Im gonna be checking this out soon. ;)

---

### Post by rolandixor on 2010-02-28
???

It doesn't work. It's trying to use images as python modules (I am not joking). I'll post the terminal output if you ask, as well as a screenshot. Please provide a .deb (it's python so it should work on 64bit) or use a ppa if you can.

It looks to be a good program, but I'm not getting anything from it. Plus the script for compiz is confusing :S I'm not a french guy at all (I barely passed it at school).

---

### Post by smo on 2010-02-28
hi

thx for the feedback

what s not working rolandixor ?

post the error please ;)

deb/ppa are coming soon

++

---

### Post by smo on 2010-02-28
hi

ok, i removed the old files from my ppa and made a basic deb

you can try the ppa:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C3BB95BB
sudo add-apt-repository ppa:s-lagui/ppa 
sudo apt-get update
sudo apt-get install gstyle


like i said, it s a basic deb, no support for cubemodel plugin in it
i just added a launcher and a .desktop file, so gstyle must be in your gnome menu after installation

:)

++

---

### Post by chaopoch on 2010-03-01
Can I still update gstyle through svn update?

---

### Post by smo on 2010-03-01
hello

no you can t chaopoch
remove your gstyle folder then check the git version or ppa ;)

remove /home/xxx/.config/gstyle too

++

---

### Post by chaopoch on 2010-03-01
> **smo said:**
> hi

ok, i removed the old files from my ppa and made a basic deb

you can try the ppa:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C3BB95BB
sudo add-apt-repository ppa:s-lagui/ppa 
sudo apt-get update
sudo apt-get install gstyle


like i said, it s a basic deb, no support for cubemodel plugin in it
i just added a launcher and a .desktop file, so gstyle must be in your gnome menu after installation

:)

++


Where is the launcher? I can not find it.

---

### Post by smo on 2010-03-02
ola

update, i made a small mistake in the .desktop

u ll have it in preferences normally now...

++

---

### Post by chaopoch on 2010-03-02
> **smo said:**
> ola

update, i made a small mistake in the .desktop

u ll have it in preferences normally now...

++

Thanks, but you forgot the icon of launcher.

---

### Post by smo on 2010-03-02
ola

??

you dont have /usr/share/pixmaps/puzzle.png

?

---

### Post by chaopoch on 2010-03-02
> **smo said:**
> ola

??

you dont have /usr/share/pixmaps/puzzle.png

?

Yes.


PS: Don't know why ? I can not upload screenshot.

---

### Post by chaopoch on 2010-03-02
I just download the deb and check, you placed the puzzle.png in /usr/share/pixmaps/data/img, I think you should place it in /usr/share/pixmaps.

---

### Post by smo on 2010-03-02
oh sorry i'll correct it it the next deb ;)

some friend are trying to port the freedesktop api to python

if ok we ll link gnome-look in gstyle maybe :)

so download/upload etc all themes from gnome-look directly in gstyle...

and for my work on fullpack, i can t find a better solution to generate gtk preview in fullpack :( so it s a bit slow...

i still have to do the edit and save/create function for it 

++

---

### Post by smo on 2010-03-02
ok i m generating a new deb

but it s anormal...

++

---

### Post by smo on 2010-04-04
ola

new version for gstyle !

- You can now add/create/edit or save fullpacks themes

we have a serie of selector with preview for each elements, gtk/icons/wallpapers... just select your themes then save or export your theme

gstyle now automatically detect and show the preview for your themes when clicking the "new" button to create a fullpack ;)

same thing when you select a fullpack theme

- the wallpaper scan engine has been rewrited a little for a better compatibility with gnome

- i added a small part in metacity to manage the butons layout
like this small software :

[http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html](http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html)

- some fixes on the gui and more ...

new .deb generated for  karmic and lucid (build pending actually...)

check it and share your fullpacks :)

++

---

### Post by smo on 2010-04-04
ola

.deb updated to fix a small bug on walldyn's xml without images in it...

++

---

### Post by smo on 2010-04-04
First post edited with the ppa infos... :)

++

---

### Post by ExiledV2 on 2010-04-22
Running Lucid 10.04 on an Acer Aspire 1410.

I am unable to get the GDM/Xsplash section to work. Neither Automatic Setup nor setting the items manually seems to operate. Applying in the GDM does not bring an error, but does not apply; preview does not function for Xsplash. Is there any information I may provide in order to determine the issue?

Note: Just tried launching it via gksudo to see if it made a difference. Result was no.

---

### Post by smo on 2010-05-11
hello

i made an update on the git version

xsplash removed, more options and fix for gdm and a new function  to change the gnome panel menu's icon

++

---

### Post by smo on 2010-05-24
hi

new deb available with a new walltime editor, gdm section rewrited and the new function to change the gnome panel menu image

waiting for returns :)

++

---

### Post by smo on 2010-05-29
hi

too much returns!!! :D ...

i just created a new deb again, we now have a new install system with a drag n drop zone to push theme's archives

it support tar|gz|bz2|lzma,zip,rar,7z... and detect icons/gtk/emerald/metacity/mouse and fullpacks theme


exemple,you take a theme from deviantart or gnome-look... you drag the file then gstyle will scan it for themes and install theme all automatically (even if other themes are compressed too)

++

---

### Post by hariks0 on 2010-05-29
Used ppa and installed. But it does not launch. I tried switching to Metacity. The same happens. The terminal output is as follows 

```
hari@Indira:~$ gstyle
Gstyle Config ok
start icons scan
start emerald scan
start metacity scan
start mouse scan
start gtk scan
start wallpapers scan
start cubemodels scan
img is not a valid cubemodel theme
start fullpacks scan
img is not a valid fullpack theme
/usr/share/gstyle/gui/main.py:36: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.wTree = gtk.glade.XML(GLADE_FILE, None ,config.APP_NAME)
/usr/share/gstyle/gui/main.py:36: GtkWarning: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed
  self.wTree = gtk.glade.XML(GLADE_FILE, None ,config.APP_NAME)
Traceback (most recent call last):
  File "gstyle.py", line 54, in <module>
    Gstyle()
  File "gstyle.py", line 48, in __init__
    self.gtk_gui.initialisation_gui(self)
  File "/usr/share/gstyle/gui/main.py", line 38, in initialisation_gui
    self.icon_obj = IconGui(self.wTree,self.gstyle_obj.icon_dict)
  File "/usr/share/gstyle/gui/icon.py", line 75, in __init__
    self.check_gconf_options()
  File "/usr/share/gstyle/gui/icon.py", line 208, in check_gconf_options

```

---

### Post by smo on 2010-05-30
hi

thanks for the return, is it the full error message?

if yes,do you have python-gconf and python-gnome2 installed?

and again if yes, what the result of the command:

gconftool-2 -g /desktop/gnome/interface/menus_have_icons

++

---

### Post by hariks0 on 2010-05-30
> **smo said:**
> hi

thanks for the return, is it the full error message?

if yes,do you have python-gconf and python-gnome2 installed?

and again if yes, what the result of the command:

gconftool-2 -g /desktop/gnome/interface/menus_have_icons

++

```
hari@Indira:~$ sudo gconftool-2 -g /desktop/gnome/interface/menus_have_icons
[sudo] password for hari: 
True
hari@Indira:~$ 
```

---

### Post by smo on 2010-05-30
ok

what s after that :

File "/usr/share/gstyle/gui/icon.py", line 208, in check_gconf_options

when you start gstyle please

---

### Post by hariks0 on 2010-06-01
```
main.py:36: GtkWarning: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed
  self.wTree = gtk.glade.XML(GLADE_FILE, None ,config.APP_NAME)
Traceback (most recent call last):
  File "gstyle.py", line 54, in <module>
    Gstyle()
  File "gstyle.py", line 48, in __init__
    self.gtk_gui.initialisation_gui(self)
  File "/usr/share/gstyle/gui/main.py", line 38, in initialisation_gui
    self.icon_obj = IconGui(self.wTree,self.gstyle_obj.icon_dict)
  File "/usr/share/gstyle/gui/icon.py", line 75, in __init__
    self.check_gconf_options()
  File "/usr/share/gstyle/gui/icon.py", line 208, in check_gconf_options
    menuicon = self.gclient.get_bool("/desktop/gnome/interface/menus_have_icons")
glib.GError: Type mismatch: Expected `bool' got `string' for key /desktop/gnome/interface/menus_have_icons
hari@Indira:~$ 

```

---

### Post by smo on 2010-06-03
hi

thanks for the infos

it might be fixed in the new deb i'm generating now

it seems that some users have problems with gdm too but i can t reproduce this bug, if someone read this post hand have the same problem please explain how/when it happen and whats the result...

maybe the /etc/gdm/custom.conf before/after the problem can help too 

thx

++

---

### Post by hariks0 on 2010-06-04
Updated this morning. Now the terminal output is:

```
hari@Indira:~$ gstyle
Gstyle Config ok
start icons scan
start emerald scan
start metacity scan
start mouse scan
start gtk scan
start wallpapers scan
start cubemodels scan
img is not a valid cubemodel theme
start fullpacks scan
img is not a valid fullpack theme
/usr/share/gstyle/gui/main.py:36: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.wTree = gtk.glade.XML(GLADE_FILE, None ,config.APP_NAME)
/usr/share/gstyle/gui/main.py:36: GtkWarning: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed
  self.wTree = gtk.glade.XML(GLADE_FILE, None ,config.APP_NAME)
Traceback (most recent call last):
  File "gstyle.py", line 54, in <module>
    Gstyle()
  File "gstyle.py", line 48, in __init__
    self.gtk_gui.initialisation_gui(self)
  File "/usr/share/gstyle/gui/main.py", line 38, in initialisation_gui
    self.icon_obj = IconGui(self.wTree,self.gstyle_obj.icon_dict)
  File "/usr/share/gstyle/gui/icon.py", line 75, in __init__
    self.check_gconf_options()
  File "/usr/share/gstyle/gui/icon.py", line 209, in check_gconf_options
    btnicon = self.gclient.get_string("/desktop/gnome/interface/buttons_have_icons")
glib.GError: Type mismatch: Expected `string' got `bool' for key /desktop/gnome/interface/buttons_have_icons
hari@Indira:~$ 

```

---

### Post by shiwlof on 2010-06-05
Same thing with me

> Gstyle Config ok
start icons scan
start emerald scan
start metacity scan
start mouse scan
start gtk scan
start wallpapers scan
start cubemodels scan
img is not a valid cubemodel theme
start fullpacks scan
img is not a valid fullpack theme
/usr/share/gstyle/gui/main.py:36: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.wTree = gtk.glade.XML(GLADE_FILE, None ,config.APP_NAME)
/usr/share/gstyle/gui/main.py:36: GtkWarning: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed
  self.wTree = gtk.glade.XML(GLADE_FILE, None ,config.APP_NAME)
Traceback (most recent call last):
  File "gstyle.py", line 54, in <module>
    Gstyle()
  File "gstyle.py", line 48, in __init__
    self.gtk_gui.initialisation_gui(self)
  File "/usr/share/gstyle/gui/main.py", line 38, in initialisation_gui
    self.icon_obj = IconGui(self.wTree,self.gstyle_obj.icon_dict)
  File "/usr/share/gstyle/gui/icon.py", line 75, in __init__
    self.check_gconf_options()
  File "/usr/share/gstyle/gui/icon.py", line 208, in check_gconf_options
    menuicon = self.gclient.get_string("/desktop/gnome/interface/menus_have_icons")
glib.GError: Type mismatch: Expected `string' got `bool' for key /desktop/gnome/interface/menus_have_icons
charl@w00kie:~$

---

### Post by chandru on 2010-06-05
I have managed to fix it by adding a new function get_bool in functions.py in the same format as get_string and change the lines 208 and 209 in icon.py to call this function.

I do not know how to submit a patch, so I hope this helps.

Regards

---

### Post by hariks0 on 2010-06-05
> **chandru said:**
> I have managed to fix it by adding a new function get_bool in functions.py in the same format as get_string and change the lines 208 and 209 in icon.py to call this function.

I do not know how to submit a patch, so I hope this helps.

Regards

You can rather post the content of the patch here.

---

### Post by chandru on 2010-06-05
There you go, my friend. I had a .txt extension to the patch to get around the upload restrictions.

---

### Post by smo on 2010-06-05
hi

damn, i changed from get_bool to get_string for you hariks0
i don t know why "true" was a string for you but it  s the problem not gstyle...( and now it s bool for you, crazy...)

i ll put get_string back and make a new deb, i ll add a check on the value type too...

thx

++

anybody with problems on gdm?

---

### Post by smo on 2010-06-05
hi

ok, we rewrited this part in another way, string or bool will be ok now...

i fixed the installation of dynamic wallpapers thru the drag n drop too

ppa updated soon (generating on launchpad now...)

++

---

### Post by ledzepjes on 2010-06-05
I wanted to know if you could add simple feature, I would greatly like to change the min, max, close buttons independently from the theme, as a currently like the new ubuntu 10.04 theme called Ambience, but I don't prefer the circular style buttons for min, max and close, aside from being on the right or left side I just use ubuntu tweak and change it from there, but I would like to select the Ambience theme with the square min max close buttons from clearlooks or human theme. Thanks, that's all.

---

### Post by smo on 2010-06-06
hi

ledzepjes, we ll maybe do that later, for the moment you can use it:

[https://launchpad.net/mct](https://launchpad.net/mct)

it s a complete metacity manager ;)

++

---

### Post by smo on 2010-06-06
hi

for users having problems with gdm, do you use gdm2setup

i have many problems with it, heres the custom.conf it generates (completely false)


[daemon]
timedloginenable = False
automaticlogin = smo
automaticloginenable = True
timedlogindelay = 0.0
timedlogin = smo


we MUST not have space between = and key/value so it fail all the config and gstyle can t read the file anymore and could make problems after...

problems iin the key names too
timedloginenable might be TimedLoginEnable
automaticlogin -> AutomaticLogin

so take care about this, i reported a bug on their ppa ;)

i have to remove the /etc/gdm/custom.conf, gstyle will recreate it

maybe we have another problem on gstyle i don t know, but i can t reproduce it

++

---

### Post by shiwlof on 2010-06-07
Thanks, Gstyle works now after doing an update with apt-get.
Let the fun begin. hehe

---

### Post by smo on 2010-06-07
hi

thx shiwlof ;)

new update for gstyle :

* add gconf option to get the home/computer/network/trash or volumes icon visible on the desktop (or not..) in the "icons" section
* add progress bar and vertical space to the gtk preview widget
* fix gtk warnings from glade
* update french locale

i just pushed the files to launchpad, new deb available in a few minutes...

all the files are now on a 1gb/s dedicated :D

we also started a thread of shareables themes created and installable thru gstyle here:

[http://forum.ubuntu-fr.org/viewtopic.php?id=400320](http://forum.ubuntu-fr.org/viewtopic.php?id=400320)

could be nice to have thread like that on this forum... ;)

++

---

### Post by yonik on 2010-06-09
gstyle don't launch: 

yonatan@yonatan-laptop:~$ gstyle
Gstyle Config ok
start icons scan
start emerald scan
start metacity scan
start mouse scan
start gtk scan
Traceback (most recent call last):
  File "gstyle.py", line 54, in <module>
    Gstyle()
  File "gstyle.py", line 35, in __init__
    self.gtk_dict = GtkDict()
  File "/usr/share/gstyle/lib/gtk.py", line 22, in __init__
    self.scan_system()
  File "/usr/share/gstyle/lib/gtk.py", line 39, in scan_system
    self.add_item_system(item)
  File "/usr/share/gstyle/lib/gtk.py", line 57, in add_item_system
    themeini.readfp(open(deskfile))
  File "/usr/lib/python2.6/ConfigParser.py", line 305, in readfp
    self._read(fp, filename)
  File "/usr/lib/python2.6/ConfigParser.py", line 482, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/yonatan/.themes/Darker theme/index.theme, line: 1
'w[Desktop Entry]\n'
yonatan@yonatan-laptop:~$

---

### Post by smo on 2010-06-09
hi

thanks for the info, i ll add a check for that, for the moment

move this theme in another folder or remove/edit it

/home/yonatan/.themes/Darker theme

could you show me the content of the index.theme file in this folder?

++

---

### Post by yonik on 2010-06-10
Thanks  so much for the solution.
I deleted  the folder.
Now I can run the  software, but I can not download anything that the list is empty.




[[IMG]http://img190.imageshack.us/img190/9093/screenshot023l.png[/IMG]]("http://img190.imageshack.us/i/screenshot023l.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by aniruddha on 2010-06-15
Hey smo, your program looks pretty neat, but after installation whenever I try starting it up I get the following output:

Gstyle Config ok
start icons scan
start emerald scan
start metacity scan
start mouse scan
You can specify only one Xcursor at a time

and the program just freezes. Any suggestions? Thanks a ton...

---

### Post by smo on 2010-06-16
hello

yonik, problem fixed? 

aniruddha, this is fixed in the next release

so, i just finished the first part of a big update!!

first, gstyle now use dbus and policykit for admin commands to be less ubuntu dependent it must normally run on debian squeeze (i haven t tested yet)

xcur2png has been removed from gstyle and i made a deb for 32/64 bits on my ppa so more problems with it (it was the most reported problem...)

i need some testers before doing a new deb


to try:

1/ remove gstyle deb if you have it

sudo apt-get remove gstyle

and install xcur2png and other dep form the first post if you never installed gstyle before (from the ppa)

2/

check the new github branch:

cd ~
git clone git://github.com/smolleyes/gstyle.git
cd gstyle
git checkout gstyle-trunk
sudo python setup.py install --install-layout=deb

done !!

you must normally have gstyle in your gnome menu ("settings" section) or by command line

:)

++

---

### Post by yonik on 2010-06-16
[COLOR=#000000]Hello.
[/COLOR][COLOR=#000000]The problem still  exists[/COLOR]-I can  not download new themes, icons, etc.

I  installed the new version, as you asked, but I did not notice the  changes.

---

### Post by smo on 2010-06-16
hello

try this:

rm ~/.config/gstyle/elements/fullpacks/img/*
rm ~/.config/gstyle/elements/cubemodel/img/*

might works since the server works fine i think ou had a corrupted image

start gstyle from the command line when you have a problem to get some infos ;)

++

---

### Post by yonik on 2010-06-16
Thanks for the answer, but I'm still having the problem.

> yonatan@yonatan-laptop:~$ gstyle
Gstyle Config ok
start icons scan
start emerald scan
start metacity scan
start mouse scan
start gtk scan
start wallpapers scan
start cubemodels scan
start fullpacks scan
/usr/lib/python2.6/dist-packages/gstyle/gui/metacity.py:169: GtkWarning: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
  self.model.append([item.name,item.path])
Current gtk theme: ClearlooksClassic
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gstyle/gui/fullpacks.py", line 273, in action_refresh
    count = refresh_themes_download(theme_list, self.fullpack_down_model, fullpack_home_srcdir)
  File "/usr/lib/python2.6/dist-packages/gstyle/functions.py", line 174, in refresh_themes_download
    img = gtk.gdk.pixbuf_new_from_file_at_scale(localimg,  100, 100 , 1)
glib.GError: &#1508;&#1493;&#1512;&#1502;&#1496; &#1511;&#1493;&#1489;&#1509; &#1514;&#1502;&#1493;&#1504;&#1492; &#1500;&#1488; &#1502;&#1494;&#1493;&#1492;&#1492;
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gstyle/gui/fullpacks.py", line 261, in action_download
    archive = geturl(self.down_link, '/tmp/'+self.down_name+'.tar.lzma', self.progress)
AttributeError: 'FullpackGui' object has no attribute 'down_link'
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gstyle/gui/fullpacks.py", line 273, in action_refresh
    count = refresh_themes_download(theme_list, self.fullpack_down_model, fullpack_home_srcdir)
  File "/usr/lib/python2.6/dist-packages/gstyle/functions.py", line 174, in refresh_themes_download
    img = gtk.gdk.pixbuf_new_from_file_at_scale(localimg,  100, 100 , 1)
glib.GError: &#1508;&#1493;&#1512;&#1502;&#1496; &#1511;&#1493;&#1489;&#1509; &#1514;&#1502;&#1493;&#1504;&#1492; &#1500;&#1488; &#1502;&#1494;&#1493;&#1492;&#1492;
gstyle.py:50: Warning: instance of invalid non-instantiatable type `(null)'
  gtk.main()
gstyle.py:50: Warning: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  gtk.main()
yonatan@yonatan-laptop:~$ 
> 

&#1508;&#1493;&#1512;&#1502;&#1496; &#1511;&#1493;&#1489;&#1509; &#1514;&#1502;&#1493;&#1504;&#1492; &#1500;&#1488; &#1502;&#1494;&#1493;&#1492;&#1492; = Unrecognized file format

---

### Post by smo on 2010-06-16
ola

woo  i have no idear .... really strange 

glib.GError: &#1508;&#1493;&#1512;&#1502;&#1496; &#1511;&#1493;&#1489;&#1509; &#1514;&#1502;&#1493;&#1504;&#1492; &#1500;&#1488; &#1502;&#1494;&#1493;&#1492;&#1492;  ??????????????

i ll look ...

++

---

### Post by smo on 2010-06-16
i added a try/except check ont the image for your bug yonik... but i can t understand..

++

---

### Post by yonik on 2010-06-16
Here is the translation of "&#1508;&#1493;&#1512;&#1502;&#1496; &#1511;&#1493;&#1489;&#1509; &#1514;&#1502;&#1493;&#1504;&#1492; &#1500;&#1488; &#1502;&#1494;&#1493;&#1492;&#1492;": Image file format not recognized.

Thank you for your effort.

---

### Post by aniruddha on 2010-06-17
Hello. After following your instructions for the new install, I am still getting the exact same error message. Here is my terminal output:

Gstyle Config ok
start icons scan
start emerald scan
start metacity scan
start mouse scan
You can specify only one Xcursor at a time

Any advice? Thanks a ton...

---

### Post by hepha on 2010-06-17
pls hellp me 
Sorry, user  is not allowed to execute '/usr/bin/gconftool-2 -g /apps/gdm/simple-greeter/disable_user_list' as gdm on lucid.


Version: 0.2+git20100617b-1
Architecture: all
Maintainer: Laguillaumie sylvain <s.lagui@gmail.com>
Installed-Size: 36
Depends: python, pygtk2, pygobject2, dbus-python, wget, python-metacity, python-beautifulsoup, python-glade2, p7zip-full, xcur2png

ubuntu not have pygtk2 this python-gtk2 ?

---

### Post by smo on 2010-06-17
hello

sorry i had some problems to create the deb sources yesterday with the new setup.py
you have a "test package"...

update your sources and upgrade

it works now, i generated another deb 1 hour ago and i ll send another one for a real fix of the aniruddha problems (i reproduced it)


Edit: ok just posted the files on the ppa, update available in a few minutes...

and, Zgegball (from the bisigi project) just showed me his new theme Eco, it s great so i added it to the fullpack list available in gstyle :)

edit:

new deb available

++

---

### Post by aniruddha on 2010-06-18
It works! 

Awesome stuff smo, will now check this out. Great work and brilliant support. Thanks a ton...

---

### Post by smo on 2010-06-18
hello

thx ;)

it  seems i have a problem with the deb on 64 bits, files are installed correctly but it can t find the libs, i search why...

++

---

### Post by nilarimogard on 2010-06-18
The latest version from the PPA doesn't start for me (32bit Lucid):


andrei@andrei-desktop:~$ gstyle
Traceback (most recent call last):
  File "gstyle.py", line 3, in <module>
    from gui.main import MainWindow
ImportError: No module named gui.main

---

### Post by smo on 2010-06-18
hello

yeah nilarimogard, i just came back at home, i know why we have this problem, i fix it and send a new deb in few minutes (not a big problem..)

edit: this bug is because __init__.py are not copied in the deb when the package is generated on the ppa... they're in my source package normally...strange, i'm adding those files to the setup.py to try...

++

---

### Post by smo on 2010-06-18
ok, the deb is good now and i had a conflict with my setup.py tries....

by security, be sure to remove this 2 folders if you have them

sudo rm -R /usr/lib/python2.6/dist-packages/gstyle
sudo rm -R /usr/lib/python2.6/site-packages/gstyle

then you can install the new deb 

thx ;)

++

---

### Post by XSAlliN on 2010-06-20
Nice, but to messy for my needs. Which leads me to the next situation... I tried the general theme manager wile checking those themes and it auto-installed the full package as this tool is intended. Manage to clean most of the content added except **.Wallpapers**...

I don't use an extra .Wallpapers folder in Home folder, but the one in usr/share/backgrounds (which is also edited for my needs). The things is, beyond that folder Gstyle also ads an extra setting for the ones instaled in .Wallpapers. Which leads me to the next question:

Where is that setting?? :confused:

Since now I have 2 sets of wallpapers (even clones), one from ../backgrounds and the other from .wallpapers. Deleting the .wallpapers folder would remove the wallpapers from default list, but I like a deep clean and would also like to remove that setting but I don't know where you set it. Could you please point me to it - tx. ):P

---

### Post by smo on 2010-06-20
hello XSAlliN

sorry but we dont  understand your "problem" could you explain it again :)

you don t like the .wallpapers?

it s possible that you see the same wallpapers 2 times in the list when you install a fullpack with an already installed wallpaper, when you restart gstyle  it will not be the case anymore, i need to fix it

for the rest i don t see where s the problem :)

++

---

### Post by XSAlliN on 2010-06-20
No it's not about that.

My default folder for wallpapers is "usr/share/backgrounds (which is the default "wallpapers folder in Ubuntu"). But it's also looked by default, so there are many that use a folder from and same goes for gstyle - since in created a .Wallpapers folder.

I don't want a wallpapers folder since I edited the default Ubuntu folder (usr/share/backgrounds) and that's where I keep my wallpapers.

The thing is, beyond that "folder" you tool ads a "setting" somewhere (related to some script in gstyle I guess), one that ads a line for each theme installed and each wallpaper added in ".Wallpapers folder.

What setting is that? What those it ads or modifies for theme backgrounds that go in .Wallpapers folder?

For example. To edit default wallpapers from usr/share/background I have to edit /usr/share/gnome-background-properties/**ubuntu-wallpapers.xml**

Where those your script generate that setting?

I also have showtime wallpaper and it also got installed with that theme and now I have clones. I guess Deleting the .Wallpapers folder would solve this problem, but since "i like to keep my system clean" I would like to remove that setting as well. I uninstalled Gstyle and all those themes, but where do I remove this "setting"? :confused:

---

### Post by smo on 2010-06-21
hello

i understand your problem but we ll not change the system...simply because more user prefer prefers to avoid the needs of admin rights (i think so)


in gnome, /usr/share/gnome-background-properties/ubuntu-wallpapers.xml
is used to list the defaut wallpapers in /usr/share/backgrounds and scan xml files in /home/xxx/.local/share/backgrounds too then finally create /home/xxx/.gnome2/backgrounds.xml, it s this file the most important and we use the same system but store our images in /home/xxx/.wallpapers (and add it to the scan..)

in the beggining of gstyle i used /usr/share/backgrounds to store the image but in debian it s not the same dir first (not a big problem..) and more important, less we need admin rights better it is ;)

maybe we could use the ~/.local/share/backgrounds to be more "clean" but not /usr

comments/idears on this problem are welcome ;)

sorry

(still sorry for my english :))

++

---

### Post by XSAlliN on 2010-06-22
Thanx.

- that's just what I needed to know. Now it's clean just how I like it. ):P 

You can set it as you will (the cleaner the better), obviously didn't advice you in editing by root rights. Just needed to clean my system of those unknown settings, which only you knew where you put it. :)

The cleanest and probably the best way would be to add them in Gstyle folder and set it (the .icons .themes and .wallpapers) so they don't interact with other appearance tools. Unless Gstyle works as a Fronted.

---

### Post by bronto64 on 2010-07-24
Hi, after install gstyle with console , the app shows in the menu and click on it but start to launch and later ends without any message or screen. Any ideas?. I use ubuntu lucid with compiz fusion icon (i don't know if this is relevant), emerald and compiz. Sorry for my bad english :)

Federico.


Solved :). I have changed with "sudo chmod +x /usr/bin/gstyle" and voila, its running now.

---

### Post by Villela on 2010-07-27
Hi everyone... 
First post "ever"... 

I'm having a trouble with Gstyle, was working very fine... suddenly I click to start it... and it doesn't at all... 

Got into terminal, and I got this: 

```
Traceback (most recent call last):
  File "gstyle.py", line 53, in <module>
    Gstyle()
  File "gstyle.py", line 37, in __init__
    self.wallpapers_dict = WallPaperDict()
  File "/usr/share/pyshared/gstyle/lib/wallpapers.py", line 58, in __init__
    self.scan_system()
  File "/usr/share/pyshared/gstyle/lib/wallpapers.py", line 80, in scan_system
    wallpapers_local = self.scan_file_xml(gstyle_background_xml)
  File "/usr/share/pyshared/gstyle/lib/wallpapers.py", line 147, in scan_file_xml
    xml_obj = minidom.parse(file_obj)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 928, in parse
    result = builder.parseFile(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
```

I found somewhere, this text: 

> Fix Gstyle doesn’t launch
Some encounter key mismatch error when launching Gsyte although it works well in my Ubuntu 10.04.
Type gstyle in terminal to launch and get the error,then try following to fox:
Press Alt+F2 and type gconf-editor in pop-up window, in next window navigate to desktop/gnome/interfaces.Right-click in right box to create a new key.In Name area type the key name in the error report,and set its type to “String”

But, "What key?" 

I'm a light bulb, in a need of energy! 

Thanks!

---

### Post by blackhock on 2010-07-27
Yes it's really awesome man :) 
Good job

---

### Post by xfearxnxloathing on 2011-03-01
i just installed today via: [http://www.ubuntugeek.com/gstyle-a-new-full-gnome-theme-manager.html](http://www.ubuntugeek.com/gstyle-a-new-full-gnome-theme-manager.html)  and cannot get it to open at all.

> hybrid@ultra:~$ gstyle
Gstyle Config ok
start icons scan
start emerald scan
Traceback (most recent call last):
  File "gstyle.py", line 53, in <module>
    Gstyle()
  File "gstyle.py", line 26, in __init__
    self.emerald_dict = EmeraldDict()
  File "/usr/share/pyshared/gstyle/lib/emerald.py", line 25, in __init__
    self.scan_system()
  File "/usr/share/pyshared/gstyle/lib/emerald.py", line 54, in scan_system
    self.add_item_system(dir)
  File "/usr/share/pyshared/gstyle/lib/emerald.py", line 86, in add_item_system
    with open(deskfile, 'wb') as configfile:
IOError: [Errno 13] Permission denied: '/home/hybrid/.emerald/themes/DarkLight/theme.ini'


and unlike cybergalvez' problem im not missing any above folder.

---

### Post by smo on 2011-03-02
hi

just change rights on the folder...

sudo chown -R hybrid:hybrid /home/hybrid/.emerald/themes

++

---

### Post by xfearxnxloathing on 2011-03-04
> **smo said:**
> hi

just change rights on the folder...

sudo chown -R hybrid:hybrid /home/hybrid/.emerald/themes

++

duuude, thnx!!!

---

### Post by gslack on 2011-03-26
Just a quick mention. Some may have errors when the program reaches the metacity part. Make sure you have the python-metacity package installed through synaptic. Seems its another dependency left out somehow. Frankly I am not going to bother with this even after getting it to run now. After installing per the instructions supplied, I still had to go and physically find and add 3 of the dependencies myself. This was not mentioned nor was it brought up during the installation or upon attempting to run it. I had to run it from the terminal, read the errors and go find the missing dependencies. Sorry but thats not a finished package IMHO. I will attempt to try it out because I have it all in now, but had I known I doubt I would have bothered. And I am sure most people (far less OCD than myself) would pass on this as well. The program does show promise though, and I hope it is finished soon.

---

### Post by smo on 2011-03-26
hi

thanks for your post, i changed my packaging system since the latest upload on my ppa... dependencies were not added to the package

i m sending new packages now...

thx 

++

---

### Post by emma00 on 2011-06-10
can anyone tell me that how to remove gstyle using terminal.It freezes my ubuntu classic 11.04.Thanks

---


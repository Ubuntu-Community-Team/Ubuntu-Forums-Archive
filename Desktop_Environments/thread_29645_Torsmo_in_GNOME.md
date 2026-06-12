---
title: "Torsmo in GNOME"
date: 2005-04-25
forum: Desktop Environments
---

### Post by zaxer on 2005-04-25
Hi guys.

Did anyone run torsmo (system monitoring) correctly in Gnome?

[http://torsmo.sourceforge.net/](http://torsmo.sourceforge.net/) 

I install it with synaptic and everything went well but it doesnt show right in my gnome desktop...

---

### Post by Stormy Eyes on 2005-04-25
[QUOTE=zaxer]I install it with synaptic and everything went well but it doesnt show right in my gnome desktop...[/QUOTE]

Torsmo's README explicitly states that Torsmo does not work with apps that take over the desktop, as Nautilus does when running with GNOME. If you want Torsmo, you can't use Nautilus to draw the desktop. You've got a choice: icons, or Torsmo.

---

### Post by zaxer on 2005-04-25
WoW

I think thats an easy choice.. I do prefer icons but still want to monitor my system.

Ive tried Gkrellm but didnt like the way it shows up the info.

Can you recommend me one?

Thanks Stormy!

---

### Post by Stormy Eyes on 2005-04-25
[QUOTE=zaxer]WoW

I think thats an easy choice.. I do prefer icons but still want to monitor my system.

Ive tried Gkrellm but didnt like the way it shows up the info.

Can you recommend me one?

Thanks Stormy![/QUOTE]

I've been using gDesklets with [Guages](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=201) to give my desktop a cool analog look.

---

### Post by tread on 2005-04-25
If you do install gdesklets, dont install the data package, which contains a lot of old non-working desklets. Just install the base package and then get the desklets you want and install them using the config tool provided by gdesklets. (This starts automatically when you start gdesklets from the gnome menu).

---

### Post by zaxer on 2005-04-25
[QUOTE=tread]If you do install gdesklets, dont install the data package, which contains a lot of old non-working desklets. Just install the base package and then get the desklets you want and install them using the config tool provided by gdesklets. (This starts automatically when you start gdesklets from the gnome menu).[/QUOTE]
 Great info!

Ill remember when installing it

Thanks Tread!

---

### Post by TopDog on 2005-04-25
You can run Torsmo without any problems in GNOME, you just need to run it as a Window:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
``` 
The downside to this is that is takes up space in the task-menu, but it works great.

See this [screenshot](http://www.pdanorway.com/gauteweb/images/linux/linux_ubuntu.jpg) as example.

---

### Post by zaxer on 2005-04-25
[QUOTE=TopDog]You can run Torsmo without any problems in GNOME, you just need to run it as a Window:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
``` 
The downside to this is that is takes up space in the task-menu, but it works great.

See this [screenshot](http://www.pdanorway.com/gauteweb/images/linux/linux_ubuntu.jpg) as example.[/QUOTE]
 Hi TopDog.

Thanks for your info but I need a little more information.

¿Where can I setup that option?

---

### Post by buellman on 2005-04-25
[QUOTE=zaxer]Hi TopDog.

Thanks for your info but I need a little more information.

¿Where can I setup that option?[/QUOTE]

is there a file like torsmorc? then maybe this helps:
[http://tao.uab.es/jao/journal/torsmorc](http://tao.uab.es/jao/journal/torsmorc)

greets. buellman

---

### Post by zaxer on 2005-04-25
Well, now the problem is I dont know where Torsmo has been installed..

---

### Post by zaxer on 2005-04-25
Ive found that file but is under a tar.gz in 

/usr/share/doc/torsmo/examples

I guess that file isnt what Im looking for...

---

### Post by buellman on 2005-04-25
[QUOTE=zaxer]Well, now the problem is I dont know where Torsmo has been installed..[/QUOTE]
try
sudo updatedb
and than
sudo locate torsmorc
or something like *torsmo* and so on...

greets. buellman

---

### Post by zaxer on 2005-04-25
These are my results when trying LOCATE for TORSMO and TORSMORC

```
/var/lib/dpkg/info/torsmo.md5sums
/var/lib/dpkg/info/torsmo.list
/var/cache/apt/archives/torsmo_0.17-4_i386.deb
/usr/share/doc/torsmo
/usr/share/doc/torsmo/changelog.Debian.gz
/usr/share/doc/torsmo/changelog.gz
/usr/share/doc/torsmo/README.gz
/usr/share/doc/torsmo/copyright
/usr/share/doc/torsmo/examples
/usr/share/doc/torsmo/examples/torsmorc.sample.gz
/usr/share/man/man1/torsmo.1.gz
/usr/bin/torsmo
/usr/local/share/man/man1/torsmo.1
/usr/local/bin/torsmo
```

```
/usr/share/doc/torsmo/examples/torsmorc.sample.gz
```

---

### Post by Nano on 2005-04-25
CONFIGURING

Default configuration file is $HOME/.torsmorc (can be changed from torsmo.c among other things). See torsmorc.sample. You might want to copy it to $HOME/.torsmorc and then start modifying it.

---

### Post by zaxer on 2005-04-25
I cant access /home/.torsmorc ...

Thats frustrating...

---

### Post by Nano on 2005-04-25
[QUOTE=zaxer]I cant access /home/.torsmorc ...

Thats frustrating...[/QUOTE]
 It doesn't exist at installation. As explained above, first you have to uncompress the sample file /usr/share/doc/torsmo/examples/torsmorc.sample.gz in your home folder with the name .torsmorc and then edit it to match your requirementss

---

### Post by zaxer on 2005-04-25
[QUOTE=Nano]It doesn't exist at installation. As explained above, first you have to uncompress the sample file /usr/share/doc/torsmo/examples/torsmorc.sample.gz in your home folder with the name .torsmorc and then edit it to match your requirementss[/QUOTE]
 Thats it.

Its running ok.

Thanks for your help Nano. Again...

---

### Post by AndersAA on 2005-04-25
put it in ~/.torsmorc

---

### Post by jazz on 2005-06-19
Hi, modify your devilspie.xml file to look like this :

```

 <devilspie> 

  <!-- 
  Hide XMMS From the Taskbar 
  -->

 <flurb>
    <matchers> 
      	<matcher name="DevilsPieMatcherWindowName"> 
        	<property name="application_name" value="XMMS"/>
     	</matcher> 
    </matchers> 
    <actions> 
      <action name="DevilsPieActionSetWorkspace"> 
        <property name="workspace_index" value="1"/> 
      </action> 
      <action name="DevilsPieActionHide"> 
        <property name="skip_tasklist" value="TRUE"/> 
      </action> 
    </actions> 
</flurb>

  <!-- 
  Hide Torsmo From the Taskbar 
  -->

 <flurb>
    <matchers> 
      	<matcher name="DevilsPieMatcherWindowName"> 
        	<property name="application_name" value="Torsmo"/>
     	</matcher> 
    </matchers> 
    <actions> 
      <action name="DevilsPieActionSetWorkspace"> 
        <property name="workspace_index" value="1"/> 
      </action> 
      <action name="DevilsPieActionHide"> 
        <property name="skip_tasklist" value="TRUE"/> 
      </action> 
    </actions> 
</flurb>
  </devilspie> 

```

And have torsmo create its own window !
There, that should solve issues with Torsmo and Gnome ! no more flickering and no more torsmo in the taskbar..

BYe,
Jazz

---

### Post by karmah on 2005-07-01
Hmm...What is this devilspie.xml ? am i supposed to create it in order to hide torsmo from taskbar and if that is the case, where do i put it?

thanks in adv.. :)

---

### Post by AndersAA on 2005-07-01
apt-cache search devilspie ;)

---


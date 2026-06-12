---
title: "New BURG themes derivated by SORA-CLEAN"
date: 2010-02-09
forum: Desktop Environments
---

### Post by ingalex on 2010-02-09
Latest version of BURG is more stable and simple [**_[COLOR="blue"]to install and to configure[/COLOR]_**]("http://www.sourceslist.eu/guide/burg-ultime-notizie/").
I've edited the official SORA-CLEAN theme for latest version of BURG. And this is the [**_[COLOR="Blue"]result[/COLOR]_**]("http://www.sourceslist.eu/guide/altri-temi-per-il-burg-basati-su-sora-clean/").

**TEMA AUTUMN**

[IMG]http://img52.imageshack.us/img52/9203/499soraedited3.jpg[/IMG]

**TEMA GOLDENSEA**

[IMG]http://img682.imageshack.us/img682/2418/499soraedited1.jpg[/IMG]

**TEMA ABSTRACT**

[IMG]http://img198.imageshack.us/img198/5923/499soraedited4.jpg[/IMG]

If you make other themes please post it.

---

### Post by ingalex on 2010-04-26
latest burg themes here: 
[LIST]
[[COLOR="Blue"]**http://www.sourceslist.eu/blog/riepilogo-temi-per-burg/**[/COLOR]]("http://www.sourceslist.eu/blog/riepilogo-temi-per-burg/")[/LIST]
[LIST]
[*][[COLOR="Blue"]**http://www.sourceslist.eu/blog/riepilogo-temi-per-burg-tabella-2/**[/COLOR]]("http://www.sourceslist.eu/blog/riepilogo-temi-per-burg-tabella-2/")
[/LIST]
:guitar:

---

### Post by P4man on 2010-04-26
It looks nice, and im sure its really easy... if you speak italian (which unfortunately, I do not). So Im left wondering what Im actually looking at. Are these grub themes?

edit: bit of googling, it turns out to be themes for BURG (which I never heard of), a grub themer if I understand correctly. Looks promising. trying it now. Those interested:
[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

---

### Post by ingalex on 2010-04-26
you can use google to translate it. These are some themes for Burg. Burg is a bootloader derivated by Grub2 and edited by [**Bean**]("http://www.burgloader.com/")
For English guides for Burg installation you can refer to this wiki **[here]("http://code.google.com/p/burg/w/list")**.
When I have some free time, I translate into English also post on my site.
It's very simple and the result is very good looking. :popcorn:

---

### Post by P4man on 2010-04-26
Just installed it on my laptop, and the  burg thing works fine, but now lucid will not longer boot in to X. Oh well, thats not your theme's fault and Ill figure it out. They do look excellent though, so Ill gladly isntall them once I actually have this working properly :)

---

### Post by ingalex on 2010-04-26
you can try to set GRUB_LINUX16 variable to "true" into  /etc/default/burg. This varible has been introduced with latest Burg revision. For more information about configurable variables and their use can refer to **[this page]("http://code.google.com/p/burg/wiki/ConfigurationVariables")**.
I've used Burg with Kubuntu Karmic and now I use it with Kubuntu Lucid and it work fine and also boot has no problem.
But if the problem persists please contact Bean on his **[forum]("http://www.burgloader.com/bbs")** for Burg project and report the problem. Sorry for my bad english. :(

---

### Post by P4man on 2010-04-26
Seems to have fixed itself. It was probably just me messing in burg editing kernel parameters. It works fine now.. even in 1400x1050 and its rather fast. Id even think faster than grub?

Anyway, now I want to install your nice themes, but the links are dead?

For instance this one:
[http://www.sourceslist.eu/?download=kubuntu_burg_theme](http://www.sourceslist.eu/?download=kubuntu_burg_theme)

---

### Post by ingalex on 2010-04-26
links are not dead it's just a temporary problem of netsons.com server where the site is hosted. I hate Netsons and i'm planning to migrato my site to another server. sorry for this drawback. retry now it should now be back fully functional.

---

### Post by P4man on 2010-04-26
Nope. I can download some of them, like the first ones (gnome theme and ubuntu wall), but not for instance the autumn burg theme or the goldensea ones.

---

### Post by ingalex on 2010-04-26
I'm trying to fix it.

---

### Post by ingalex on 2010-04-26
problem solved. now you can retry.

---

### Post by P4man on 2010-04-26
Downloads work now. I tried the gnome one (first on your site) and it looks fabulous; except I dont find it very clear to see which item is selected. Perhaps you should add a different color background to the icon or in some other way highlight it. If you look at the screen without using keys, no one will be able to tell which item is actually selected (unless you really know the theme).

I also tried goldensea one, and no icons are showing up at all?

**edit**: I fixed it by changing the icons file in icons folder. It has all OS's starting with uppercase, changing it lowercase fixes it.
still the same the complaint as for the other one though ;)

**edit bis**: an icon for ubuntu recovery would be most welcome too!

But it does look very good!

---

### Post by ingalex on 2010-04-26
Gnome theme has not been realized by me but by the administrator of [http://fuorichiave.blogspot.com/](http://fuorichiave.blogspot.com/).
For goldensea theme is very strange that icons are not displayed.
I'm using it. What operating system do you have installed?
To display the correct icon you have to define the correct class into /boot/burg/burg.cfg. Each class correspond to an O.S.
The class defined into /boot/burg/burg.cfg must correspond to the class defined into /boot/burg/themes/goldensea/icons/icons

```
menuentry "Ubuntu GNU/Linux, with Linux 2.6.32-21-generic" [COLOR="Red"]**--class kubuntu**[/COLOR] --class gnu-linux --class gnu --class os --group group_main {
	set gfxpayload=keep
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 96da9978-eb5e-4379-878b-bb5d21aa1c8f
	echo	Loading Linux 2.6.32-21-generic ...
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=96da9978-eb5e-4379-878b-bb5d21aa1c8f ro  quiet splash
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu GNU/Linux, with Linux 2.6.32-21-generic (recovery mode)" [COLOR="red"]**--class kubuntu**[/COLOR] --class gnu-linux --class gnu --class os --group group_main {
	set gfxpayload=keep
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 96da9978-eb5e-4379-878b-bb5d21aa1c8f
	echo	Loading Linux 2.6.32-21-generic ...
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=96da9978-eb5e-4379-878b-bb5d21aa1c8f ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)"  **[COLOR="Red"]--class windows[/COLOR]** --class os {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 963044e03044c8c7
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

---

### Post by P4man on 2010-04-26
See my edits above. This is icons file in /boot/burg/themes/goldensea/icons/icons :

class {
 ** K**ubuntu { image = "$$/kubuntu.png:$$/kubuntu-desktop.png" }
  **K**ubuntu1 { image = "$$/kubuntu.png:$$/kubuntu-recovery.png" }
  **U**buntu { image = "$$/ubuntu.png:$$/ubuntu-desktop.png" }
  Ubuntu1 { image = "$$/ubuntu.png:$$/ubuntu-recovery.png" }
  Memtest { image = "$$/memtest.png:$$/memtest-desktop.png" }
  Linux { image = "$$/button-linux.png:$$/button-linux-hover.png" }
  MacOSX { image = "$$/macosx.png:$$/leopard-desktop.png" }
  Windows { image = "$$/windowsxp.png:$$/windowsxp-desktop.png" }
  unknown { image = "$$/unknow.png:$$/Unknow-desktop.png" }
  Windows1 { image = "$$/windows7.png:$$/windows7-desktop.png" }
  Windows2 { image = "$$/vista.png:$$/windows_vista-desktop.png" }
}

Changing the OS names to lowercase makes it work fine.

---

### Post by ingalex on 2010-04-26
Yes good! but you can alternately change the names of class to uppercase into /boot/burg/burg.cfg. It's the same. The only difference is that each time you execute "sudo update-burg", burg.cfg will be regenerated and you loose all chages that you have made to this file.

---

### Post by P4man on 2010-04-26
The other difference is that it will probably break all other themes no?

---

### Post by ingalex on 2010-04-26
Yes it's correct. But you have found this association of class because Bean (author of BURG) has recently changed it. So some themes cointain an old association. But it's very simple to edit it.

---

### Post by universi on 2010-05-18
> **P4man said:**
> See my edits above. This is icons file in /boot/burg/themes/goldensea/icons/icons :

```
class {
 ** K**ubuntu { image = "$$/kubuntu.png:$$/kubuntu-desktop.png" }
  **K**ubuntu1 { image = "$$/kubuntu.png:$$/kubuntu-recovery.png" }
  **U**buntu { image = "$$/ubuntu.png:$$/ubuntu-desktop.png" }
  Ubuntu1 { image = "$$/ubuntu.png:$$/ubuntu-recovery.png" }
  Memtest { image = "$$/memtest.png:$$/memtest-desktop.png" }
  Linux { image = "$$/button-linux.png:$$/button-linux-hover.png" }
  MacOSX { image = "$$/macosx.png:$$/leopard-desktop.png" }
  Windows { image = "$$/windowsxp.png:$$/windowsxp-desktop.png" }
  unknown { image = "$$/unknow.png:$$/Unknow-desktop.png" }
  [COLOR="red"]Windows1[/COLOR] { image = "$$/windows7.png:$$/windows7-desktop.png" }
  [COLOR="red"]Windows2[/COLOR] { image = "$$/vista.png:$$/windows_vista-desktop.png" }
}
```

Changing the OS names to lowercase makes it work fine.

The icon of Windows 7 was not correctly recognized. It appears the Windows Xp one. So i've modified the file **/etc/burg.d/30_os-prober**, adding those few lines.

```
s=`echo :${GRUB_CLASS_OVERRIDE}: | sed "s,.*:${DEVICE}=\([^:]*\):.*,\1,"`
  if test "x$s" != "x:${GRUB_CLASS_OVERRIDE}:" ; then
    OSLABEL="$s"    
  fi
 
[B]#MODIFY OSLABEL FOR WINDOWS VISTA, SEVEN 
  case ${LONGNAME} in
  Windows?Vista*)	
	OSLABEL=[COLOR="Red"]windows2[/COLOR]            
	;;
  Windows?7*)		
	OSLABEL=[COLOR="red"]windows1[/COLOR]	
	;;
  esac
  get_auth_option ${OSLABEL}
[/B]
  echo "Found ${LONGNAME} on ${DEVICE}" >&2

```

Remember... windows2, windows1, window in LOWERCASE!

:)

---

### Post by Ms_Angel_D on 2010-05-18
Moved from Testimonials & Experiences.

---

### Post by ingalex on 2010-05-19
> **universi said:**
> The icon of Windows 7 was not correctly recognized. It appears the Windows Xp one. So i've modified the file **/etc/burg.d/30_os-prober**, adding those few lines.

```
s=`echo :${GRUB_CLASS_OVERRIDE}: | sed "s,.*:${DEVICE}=\([^:]*\):.*,\1,"`
  if test "x$s" != "x:${GRUB_CLASS_OVERRIDE}:" ; then
    OSLABEL="$s"    
  fi
 
[B]#MODIFY OSLABEL FOR WINDOWS VISTA, SEVEN 
  case ${LONGNAME} in
  Windows?Vista*)	
	OSLABEL=[COLOR="Red"]windows2[/COLOR]            
	;;
  Windows?7*)		
	OSLABEL=[COLOR="red"]windows1[/COLOR]	
	;;
  esac
  get_auth_option ${OSLABEL}
[/B]
  echo "Found ${LONGNAME} on ${DEVICE}" >&2

```

Remember... windows2, windows1, window in LOWERCASE!

:)

You could notify this editing to the [**[COLOR="Red"]official forum[/COLOR]**]("http://www.burgloader.com/bbs/") of burg. In this way Bean (author of Burg) could integrate it into Burg. So this can be usefull to more people. :)

---

### Post by ingalex on 2010-11-13
Released burg-manager 1.0.0 with new features:
[http://www.sourceslist.eu/burg-2/burg-manager/burg-manager-1-0-0-released/]("http://www.sourceslist.eu/burg-2/burg-manager/burg-manager-1-0-0-released/")

---

### Post by ShadowHawkDav on 2010-11-24
Hi there, 
  I just discovered burg and now I am trying to install the burg manager but when I click on the link I get a page telling me access is denied.  I have tried access wilth multiple computers from multiple locations but nothing seems to work. Any ideas?

---

### Post by ingalex on 2010-11-26
I've migrated the site to another hosting. Now the site is online.

---

### Post by ShadowHawkDav on 2010-11-28
Thanks, I am going to try it now.  Looks like a great program.  Do you have any suggestions on resources to create themes of my own?

---

### Post by ingalex on 2010-11-29
there are very much post about this topic on my site :-)

---

### Post by h4uw1n3 on 2011-02-23
Hey, guys...
i was trying to modify these theme also...
but,i got confused when i trying to used another image...
some was working and some aren't...
i was modify coffee theme... any idea about the image that used on burg...
first i thought,that might be the size... then i resize it, but it didn't change anything...
even so... the png file using by winter themes a lot large than mine... >600kb
so i trying again with the image size...it didn't change anything also....
i trying 1024x7xx, 640x480, 800xx600.... nothing seems working....
my screen actually 1024x600, i trying with this size... it didn't work also...
:confused::confused::confused::confused::confused:

is it might be about the image color type? or something?
i trying to login in burgloader, but no activication email come... -___-"

so... how to change it then? i don't like using bmp or png file... cause this format have a large file size....

also im using photoshop cs 8 or something,to edit this image....

thanks for ur help....

---

### Post by ingalex on 2011-05-26
[SIZE="4"]Super-boot-manager released:
[http://www.sourceslist.eu/blog/released-super-boot-manager-0-6-1-4/](http://www.sourceslist.eu/blog/released-super-boot-manager-0-6-1-4/)
[http://www.sourceslist.eu/blog/linux-blog/super-boot-manager-buc-version-download-installation/](http://www.sourceslist.eu/blog/linux-blog/super-boot-manager-buc-version-download-installation/)[/SIZE]

---

### Post by ryanh06 on 2011-05-26
> **ingalex said:**
> Latest version of BURG is more stable and simple [**_[COLOR="blue"]to install and to configure[/COLOR]_**]("http://www.sourceslist.eu/guide/burg-ultime-notizie/").
I've edited the official SORA-CLEAN theme for latest version of BURG. And this is the [**_[COLOR="Blue"]result[/COLOR]_**]("http://www.sourceslist.eu/guide/altri-temi-per-il-burg-basati-su-sora-clean/").

**TEMA AUTUMN**

[IMG]http://img52.imageshack.us/img52/9203/499soraedited3.jpg[/IMG]

**TEMA GOLDENSEA**

[IMG]http://img682.imageshack.us/img682/2418/499soraedited1.jpg[/IMG]

**TEMA ABSTRACT**

[IMG]http://img198.imageshack.us/img198/5923/499soraedited4.jpg[/IMG]

If you make other themes please post it.

I loveeeeee Burg and I love those new shiny themes!! Thanks!! [that is best read in the voice of Agnes from Despicable Me!]

---

### Post by underdog012 on 2012-08-19
> **universi said:**
> The icon of Windows 7 was not correctly recognized. It appears the Windows Xp one. So i've modified the file **/etc/burg.d/30_os-prober**, adding those few lines.

```
s=`echo :${GRUB_CLASS_OVERRIDE}: | sed "s,.*:${DEVICE}=\([^:]*\):.*,\1,"`
  if test "x$s" != "x:${GRUB_CLASS_OVERRIDE}:" ; then
    OSLABEL="$s"    
  fi
 
[B]#MODIFY OSLABEL FOR WINDOWS VISTA, SEVEN 
  case ${LONGNAME} in
  Lenovo?Recovery?Partition*)    [COLOR=Red]<----------ATTENTION!!!!!!! I also change this line FROM Windows?Vista* TO Lenovo?Recovery?Partition*  [/COLOR]
    OSLABEL=[COLOR=Red]qdrive[/COLOR]                        [/B]**[COLOR=Red]<----------ATTENTION!!!!!!! I also change this line [/COLOR]**[COLOR=Red]**as well.**[/COLOR]
[B]     ;;
  Windows?7*)        
    OSLABEL=[COLOR=red]windows[/COLOR]    
    ;;
  esac
  get_auth_option ${OSLABEL}
[/B]
  echo "Found ${LONGNAME} on ${DEVICE}" >&2

```Remember... windows2, windows1, window in LOWERCASE!

:)

         I have made a custom icon for burg loader for my Lenovo Recovery Partition.I have made 3 icons :
  
**large_qdrive.png (128 X 128 pixels)                                                                            **[IMG]http://img89.imageshack.us/img89/8692/largeqdrivevx.png[/IMG]
[B] 

small_qdrive.png (24 X 24 pixels)                                                                                                [/B][IMG]http://img341.imageshack.us/img341/5757/smallqdrive.png[/IMG]
[B] 
grey_qdrive.png  (128 x 128 pixels)                                                                               [/B] [IMG]http://img706.imageshack.us/img706/3017/greyqdrive.png[/IMG]


The .png icons that I created I made them using gimp from a **qdrive.ico** file that I found in the Lenovo Recovery Partition.
  I transferred the icons to the /boot/burg/themes/icons folder and I added to the class list of the grey,large,small and the hover files the following  lines :
  
[COLOR=Red]***-qdrive { image = "$$/large_qdrive.png" }***[/COLOR] in the large file 
[COLOR=Red]***-qdrive { image = "$$/small_qdrive.png" }***[/COLOR] in the small file  
[COLOR=Red]***-qdrive { image = "$$/grey_qdrive.png" }***[/COLOR] in the grey file 
[COLOR=Red]***-qdrive { image = "$$/grey_qdrive.png:$$/large_qdrive.png" }***[/COLOR] in the hover file   

I ran **sudo update-burg** and after that I modified the following line in the **burg.cfg** file :
  
**menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {   **

                                                                **to** 

_[COLOR=Red]***menuentry "Windows 7 (loader) (on /dev/sda2)" --class qdrive --class os {   ***[/COLOR]_
                                                             
                                                                and I also tried to change the title for the Lenovo Recovery Partition,so I tried this as well:

*[COLOR=Red]_**menuentry "Lenovo Recovery Partition (on /dev/sda2)" --class qdrive --class os {   **_[/COLOR]*

None of this tries actually enforced burg loader to use the custom icon that I made and I can't figure out why.
  I have to mention also that there are a few themes that I have installed in burg which actually are able to use the **small_qdrive.png** icon that I made,but all the others which use either the **large_qdrive.png** or the **grey_qdrive.png** weren't able to use the custom icons.
  I have double checked for typos in all the files that I have created  or I modified,so I am pretty sure that I haven't misspelled anything.
  I have checked also the title of the custom icons that I made and neither of them have a typo.
  I have looked also if there are any other folder that the themes  might use to retrieve the icons,but it seems that all of them except for ***Fortune*** theme,which I downloaded from ***OMG!UBUNTU***,use the icons folder which is located in** /boot/burg/themes/icons **
  
I tried to add the custom icons to the icons folder of the theme Fortune,but still nothing happened.


I did also the modification above in the quote and unfortunately nothing happened.I have spent over 3 hours overall to fix it,but still can't figure out what is going on!


Please help!!
[-o<

I have also posted my question to [COLOR=SeaGreen]***[AskUbuntu]("http://askubuntu.com/questions/177337/burg-custom-icons-work-only-with-specific-themes")***[/COLOR] as well.

---


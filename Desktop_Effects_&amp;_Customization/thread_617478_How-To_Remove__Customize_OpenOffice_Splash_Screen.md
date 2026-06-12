---
title: "How-To: Remove / Customize OpenOffice Splash Screen"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by Arthur Archnix on 2007-11-19
Currently this How-To has been tested using Ubuntu 7.10 & OpenOffice 2.3.0. Unfortunately, I can offer no personal opinion on how well it will work for other versions (e.g,, 6.06, 6.10, 7.04. 8.04) or other flavours (e.g,, Ku/Xu/Edu-buntus). However, if you have success with any other version or flavour, please comment about your flavour/version and what tip(s) worked.

This 'How-To' is a work in progress. My goal is to continue to update it with the tips & tricks that are personally appealing to me in using OpenOffice in Ubuntu. If you have a tip or trick that you feel is worthy of adding please feel free to post it in the comments. 

You'll find acknowledgements at the end of this post.

1. Customize (or remove) the OpenOffice Splash Screen.
2. Improve the speed/responsiveness of OpenOffice.
3. Share files with Windows Users, without installing Microsoft Fonts
4. Kill OpenOffice if it freezes up on you
5. Configure a laptop's touchpad so that it doesn't interfere with your typing


*------------------------------------------------------------------------------------------------------------------------------------------------------------------------*
**1. Customizing (or removing) the Splash Screen**

The OpenOffice splash screen is located at /usr/lib/openoffice/program/openintro_ubuntu.bmp

To change the default splash screen you only need to replace this file with your own. Make a backup of the current file:
```
sudo cp /usr/lib/openoffice/program/openintro_ubuntu.bmp /usr/lib/openoffice/program/openintro_ubuntu.bak

```Now, you can either edit the splash.bmp file using Gimp or some other program, or you can copy some other image in there. Like me, you may find it's best to maintain the dimension of the original image (440 x 286 pixels), but feel free to experiment.  

I've edited an OpenOffice bmp file to match those dimensions, which you can get [here]("http://a.imagehost.org/download/0027/openintro_ubuntu.bmp"). 

If you download this file to your desktop, you would do the following to set it as your new splash screen:
```
sudo cp ~/Desktop/openintro_ubuntu.bmp /usr/lib/openoffice/program/

```That's it. Because the example file size is smaller (in kb's) than the default, you may also notice a slightly faster load time.

If you simply wish to disable the splash screen entirely, open /etc/openoffice/sofficerc and change "Logo=1" to "Logo=0". You can open sofficerc by doing this:
```
gksudo gedit /etc/openoffice/sofficerc
```You can find more OpenOffice splash screen artwork [here]("http://marketing.openoffice.org/art/galleries/marketing/splashscreens/"). 

Additionally, ubuntuforums member [ Exploder]("http://ubuntuforums.org/member.php?u=281694") has come up with a very professional looking splash screen available in this [thread]("http://ubuntuforums.org/showthread.php?t=595207&highlight=openoffice+splash").

Lastly, if you care to you can change the graphic shown in "About" (available in OpenOffice's Help menu) by replacing the "openabout_ubuntu.bmp". It's located in the same folder as above, and you can use those same directions to backup and replace it.


*------------------------------------------------------------------------------------------------------------------------------------------------------------------------*
**2. Improving the speed / responsiveness of OpenOffice**

OpenOffice is not AbiWord, nor Gnumeric. Attempts to make it so will leave you disappointed, but there are a few things you can do to make it more responsive.

First, if you don't use *Base*, or various Wizards, or save files in certain formats like portable excel, palm, docbook, or pocket word, then disable Java. Go to: >Tools  >Options...  >Java,  then uncheck "Use a Java Runtime Environment". 

For a complete list of what OpenOffice features require Java, see [here]("http://wiki.services.openoffice.org/wiki/Java_and_OpenOffice.org"). 

Second, under >Options... >Memory, reduce the number of undo steps to a more reasonable number (somewhere between 15 and 30), change OpenOffice graphics cache to 64MB (if you have more than 1GB of RAM and a decent video card you can try upping this even higher, to say 128MB), and change memory per object to 8MB.

On older versions of OpenOffice, the Cache for number of inserted objects may be unreasonably high. The new default is 20, and this is what most resources on the web advise as well.

Some also recommend checking Enabling systray quickstart. This gives the appearance of making OpenOffice more responsive, but only by forcing itself upon Ubuntu to make OpenOffice start slightly faster. If the first thing you do everytime you start Ubuntu is open up a document, then by all means enable quickstarter, otherwise I'd leave the details of what to put into your systems memory up to Ubuntu.


*------------------------------------------------------------------------------------------------------------------------------------------------------------------------*
**3. Share documents with Windows Users, without installing Microsoft Fonts**

RedHat developed a set of fonts that, typographically speaking, act as a replacement of Microsoft's most commonly used fonts, Ariel and Times New Roman. You can read more about them [here]("https://www.redhat.com/promo/fonts/"). I've used them for some time now and I've found that my documents that I create in OpenOffice Writer are rendered exactly as I intended when opened up in Microsoft Word. If you wish to avoid having to sully your sleek Ubuntu with Miscreant Fonts, download and install the Liberation .ttf fonts [here]("https://www.redhat.com/f/fonts/liberation-fonts-ttf-3.tar.gz").

Assuming you've downloaded and extracted the font files to your desktop, in a folder named "Fonts", you can install them by doing the following:
```
sudo mkdir /usr/share/fonts/truetype/myfonts
sudo mv ~/Desktop/Fonts/*.ttf /usr/share/fonts/truetype/myfonts
sudo fc-cache -f -v
```At this point you can delete that Fonts directory from your Desktop, open OpenOffice, and go to >Tools  >Options...  >OpenOffice.org  >Fonts, and check 'Apply replacement table'

Under Font, type (without quotes) "Times New Roman", then under 'Replace With', scroll down to "Liberation Serif". Check both boxes under 'Always' and 'Screen' then click 'Ok' to apply. For Ariel, type "Ariel", and replace with "Liberation Sans". Check both boxes and apply by clicking 'OK'.


*------------------------------------------------------------------------------------------------------------------------------------------------------------------------*
**4. Kill OpenOffice if it freezes up on you**

Beware that you may very well lose any information that you have open at the time. This is to be used only as a last ditch effort, after which, you must hope that the OpenOffice document recovery feature will retrieve any lost info.

First, type this in a terminal:
```
ps ax 
```Scroll through the list and look for the OpenOffice entry. For example,
>  8645 ?        S      0:01 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -l
 8678 ?        S      0:00 kio_file [kdeinit] file   
**10348 ?        S      0:00 /bin/sh /usr/lib/openoffice/program/soffice -writer -**
10402 pts/1    Ss     0:00 bash
**10429 ?        Sl     0:01 /usr/lib/openoffice/program/soffice.bin -writer -spla**
10549 pts/1    R+     0:00 ps ax
22688 ?        S      0:00 /bin/sh /usr/bin/firefox
22702 ?        S      0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/fire
22708 ?        Sl     0:54 /usr/lib/firefox/firefox-binOnce you've found the process numbers type them into the console after the 'kill command'. E.g,,
```
kill 10429
```Even though there were two OpenOffice entries, this one kill command removes them both. If after issuing your kill command with the process number OpenOffice is still running, repeat the 'ps ax' command and kill the remaining processes until OpenOffice is no more.


*------------------------------------------------------------------------------------------------------------------------------------------------------------------------*
**5. Configure Laptop's touchpad so that it doesn't interfere with typing**

There's two things I like to do to my touchpad so that it doesn't jump around the screen and mess things up while I'm typing. First, I install "gsynaptics" from the Community (I believe) repository. This lets you configure how sensitive the touchpad is to touch. In order to use it you'll have to add an option to your xorg.conf. First back it up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```Then open it up and add this under where it says "Input Device", Identifier "Synaptics Touchpad".
```
"Option     "SHMConfig"     "true"
```For example, this is what mine looks like after adding the line:> 
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
    Option        "SHMConfig"         "true" You'll need to restart 'X' to before customizing it somewhat, you can do this with a simple Ctrl+Alt+Backspace.

The other thing to do is to turn off your touchpad while typing. You can do this by adding a new start-up program to your session. Go to >Administration  >Preferences  >Sessions, and click Add, The name could be "Touchpad Typing Monitor", or something else. The command is "syndaemon -i 1 -d", minus the quotes. You can try other numbers in there, other than 1. The number is the number of seconds to keep the touchpad disabled after typing stops.  And any description will do. I used "Disables touchpad while typing".


*------------------------------------------------------------------------------------------------------------------------------------------------------------------------*
*-------------------------------------------------------------------ACKNOWLEDGEMENTS-------------------------------------------------------------------*
*------------------------------------------------------------------------------------------------------------------------------------------------------------------------*

Thanks to [Mais]("http://ubuntuforums.org/member.php?u=27038"), for his [post]("http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad") on how to disable the Synaptics touchpad.

---

### Post by sup on 2008-03-05
there is a type /ect/openoffice/sofficerc should be /etc/openoffice/sofficerc
otherwise, thanks, splash screens are evil:-)

---

### Post by Arthur Archnix on 2008-03-05
I had trouble finding it even after you told me what to look for. I may be mildly dyslexic. :) Should be fixed now though, thanks.

---

### Post by Andrew.Z on 2008-03-16
> **Arthur Archnix said:**
> 
[/code]Now, you can either edit the splash.bmp file using Gimp or some other program, or you can copy some other image in there. Like me, you may find it's best to maintain the dimension of the original image (440 x 286 pixels), but feel free to experiment.  

There are [restrictions](http://www.oooninja.com/2008/03/change-remove-splash-screen.html) on pixel depth.  32-bit looks ugly, but 24-bit is OK.  

> You can find more OpenOffice splash screen artwork [here]("http://marketing.openoffice.org/art/galleries/marketing/splashscreens/"). 

Here is a list of pre-made [OpenOffice.org splash screens](http://www.oooninja.com/2008/03/change-remove-splash-screen.html).

> Additionally, ubuntuforums member [ Exploder]("http://ubuntuforums.org/member.php?u=281694") has come up with a very professional looking splash screen available in this [thread]("http://ubuntuforums.org/showthread.php?t=595207&highlight=openoffice+splash").

The link at gnome-files does not work.


> RedHat developed a set of fonts that, typographically speaking, act as a replacement of Microsoft's most commonly used fonts

Until they catch up, you will also need to [install Office 2007 fonts](http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html) to read Office 2007 [.docx, .xlsx, and .pptx files](http://www.oooninja.com/search/label/openxml).

> I've found that my documents that I create in OpenOffice Writer are rendered exactly as I intended when opened up in Microsoft Word.


Depending on some settings, they are not perfectly equivalent.  See [Metric Equivalent Fonts and Font Substitution ](http://www.oooninja.com/2008/02/metrical-equivalent-fonts-and-font.html).

Also, sometimes [font fallback](http://www.oooninja.com/2008/02/metrical-equivalent-fonts-and-font.html) may be automatic.  IIRC, the newer OpenOffice.org 2.4 has automatic fallbacks such as Times New Roman==Liberation Serif.

---


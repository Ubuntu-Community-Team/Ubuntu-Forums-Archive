---
title: "Netbook Remix Components w/ Dell's Mini OS"
date: 2008-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DjFIL on 2008-10-16
Hello.  I just got my Dell Mini 9 and I'm loving the variant of netbook remix that it comes with, the launcher is really nice.  I earlier played around with the official Canonical Netbook Remix via VMware on my Mac... there's a few features from it that I really liked.  I basically wanted everything except the launcher.  So I've installed the human-netbook-theme, window-picker-applet and maximus.  Note: i noticed dell's mini os was already using the maximus applet, but appeared to be an older version.  I think it should had succesfully installed the new maximus from canonical over the old dell version.  I've gotten the theme and the window picket applet to work just great... but for some reason maximus isn't giving the same results i expect it to.  I still have the menu title bar of each application showing.  Any suggestions how to fix this... here's the screenshot of what i've done below... but see the orange title bar is still there... any tips?  thanks.

[IMG]http://members.shaw.ca/djfil/Screenshot1.png[/IMG]

---

### Post by treris on 2008-10-17
First off, are you sure maximus is running? It has a habit of silently crashing every now and again with some apps. 
On my computer for instance, maximus crashes every time I use vlc, but there's no notification so you'll probably have to start the gnome-system-monitor to check.

If maximus is not running, you may also want to check whether maximus is set up to run upon boot, there should be an entry for maximus in the sessions part of your settings. Make sure that even if it is there, it's pointing at the right file.
 
Secondly, if you look up the configuration for maximus using gconf-editor (you'll find it under Apps ->Maximus) there is an option there that's called 'undecorate'. Make sure that that option is checked. 
If it wasn't then that was probably your problem, you may have to restart maximus to get the setting to work.

Allright hope that solves it,

Enjoy your mini 9!

---

### Post by njpatel on 2008-10-17
> **DjFIL said:**
> <snip>... but for some reason maximus isn't giving the same results i expect it to.  I still have the menu title bar of each application showing.  Any suggestions how to fix this... here's the screenshot of what i've done below... but see the orange title bar is still there... any tips?  thanks.


Hey, the problem your seeing is that the Dell product set's a gconf key for maximus to _not_ undecorate windows. You can easily change this by opening gconf-editor, navigating to the /apps/maximus folder, and checking the "undecorate" option on the right.

Maximus should undecorate everything straight away, but it may be useful to logout/login just in case ;-).

If you get an error sometimes where windows don't maximise fully vertically, be sure to install the metacity package from the netbook-remix-team ppa too, it has fixes for that.

I hope that helps!

---

### Post by treris on 2008-10-17
> **njpatel said:**
> If you get an error sometimes where windows don't maximise fully vertically, be sure to install the metacity package from the netbook-remix-team ppa too, it has fixes for that.


I did have that problem up until a while back, but somehow never put it together with the metacity update (obviously didn't look at the version information before updating).

Thanks so much for that fix to metacity because that bug was quite annoying!

BTW: nice to see *the* developer of the whole netbook remix taking the time to answer a question on these forums!

---

### Post by DjFIL on 2008-10-17
thank you so much for the responses.  i've found and enabled the maximus options in the gconf-editor, a reboot didn't change anything though.  the service does appear to be running, but says it's sleeping.  i tried to install on top the metacity from the netbook-remix-team ppa, but it says i already have the newest version.  here's more of the settings i'm seeing if they help.

session preferances > current session:

order 50, style 'restart', state shows 3 gears (running i think), maximus is the app ofcourse.

details from gconf-editor for maximus:

binding:  Super_L
exclude class:  [totem,wfica_seamless,ktuberling,gnometris,cheese,kwordquiz]
undercorate:  checked on.

thanks for assistance.
philip p

---

### Post by treris on 2008-10-17
Ok I'm puzzled, your settings would appear to be in order, other than that I don't have a binding set up for maximus, with me it just says 'disabled'.
Perhaps that binding disables maximus everytime you press the 'windows' button on your keyboard, I really don't know I'm afraid, but you could try disabling the binding.

Could it also be that you have various KDE applications installed? Your list of excluded classes is very much different from mine.

Perhaps uninstalling maximus (incl the configuration files) and then installing it again might help.....

Sorry I can't be of more help.

PS where are you located? Your screenshot showed a temperature of 0 degrees F.?????

---

### Post by DjFIL on 2008-10-17
oops... i tried to uninstall the old and reinstall the new metacity using apt-get purge and then install... i totally pooched my os.  so it's now restored and started again, but back to the same level where i let off.  and yeah I noticed the dell loaded a bunch of kde and gnome applications, even though the main interface is totally based on gnome, but i dunno if that'd make a difference.  if there's any other suggestions that'd be great... it's not major, but i'd really like it to work the way i exected so i can get that little bit of real estate back as every bit counts on this netbook.  thanks.

i'm in nanaimo, bc... i don't think it updated when i took that screenshot as it was about 9 degrees C that day.

---

### Post by treris on 2008-10-17
Glad you were able to restore your system, did you try taking out that binding for maximus in gconf-editor?

I would expect that binding to be towards the go-home-applet, but not maximus itself.

Other than that I'm fresh out of ideas unfortunately.

PS 9 degrees C or 0 degrees F, it does make all the difference :)

---

### Post by DjFIL on 2008-10-17
thanks again for response... and yeah, our summer is done for here, it was a nice one while it lasted but been getting chilly over past week or so.

can you please explain for me about taking out the binding for maximus?  not sure i understand how.  also the go-home-applet of netbook remix was never installed and no entry for go-home-applet is found in gconf-editor.

thanks.

EDIT... oh, wait i might had found it... the binding meaning under maximus settings in gconf-editor it has the binding for 'Super_L'?  i did try and remove that... rebooted... it hasn't changed anything with the appearance.  if that's what you were suggesting at least.  thanks again.

---

### Post by treris on 2008-10-17
Sure, 

You've looked up the settings for maximus before, right? There you saw (in the gconf-editor) that maximus had a binding to the Super_L key (which on most computers is the key with the windows sign on it, I don't know whether Dell changed that for the mini9 ubuntu edition, but probably it is still there)

If you double click on the line where it says Super_L you'll be able to edit it, just replace 'Super_L' with 'disabled' (without the apostrophes of course).
That should disable the key binding and might solve your problem. As far as the go-home-applet goes, I'd think that should be installed along with the original installation. Isn't that the applet in the left corner of your top panel? Next to the Ubuntu logo? 

From looking at a picture of the dell version of the netbook-remix in a review I now get the feeling that the Dell version of the netbook-remix is considerably different from the ubuntu-netbook-remix out of the ubuntu-netbook-remix ppa that I've been using.

Maybe Neil (njpatel) could be of some assistance here as he is involved with the actual development of the netbook-remix. Maybe he is more aware of the differences between the two versions of the netbook-remix?

---

### Post by DjFIL on 2008-10-17
yeah, thanks for the suggestions again.  i this time saved it as 'disabled', instead of blank like i tried the first time, but even after a reboot it doesn't change.  and yeah that's the go-home-applet, i thought you meant it'd be listed in the gconf-editor.  thanks again for suggestions.  hopefully neil may beable to reply and give further insight regarding my attempt to use that applet.  i really like the dell main interface, here's the screenshot of mine after i finished reorganizing all the folders and content.

[IMG]http://members.shaw.ca/djfil/Screenshot2.png[/IMG]

---

### Post by treris on 2008-10-17
Hi again, 

Sorry I couldn't help out more. Yeah that top bar that Dell uses is very nice. 
I'm working with the netbook-remix version from the ppa, which, after some modifications looks like this: 
[http://picasaweb.google.com/treris/Webshare#5258239172718974514](http://picasaweb.google.com/treris/Webshare#5258239172718974514)

Hope everything'll work out for ya, if I see anything related to this I'll let you know through either this thread or a private message.

Let me know when you find out what the problem was, I'm really curious now.

---

### Post by DjFIL on 2008-10-17
Yeah.  I was playing around with the official Canonical Netbook Remix... i liked it, but i like the main launcher of dell more... but i really loved the maximus and window-picker-applet.  glad i got window picker working fine... hope i can get maximus working too.  thank you so much for your suggestions.

---

### Post by treris on 2008-10-17
You're welcome, oh and by the way, welcome to the forums!

---

### Post by njpatel on 2008-10-18
Hey guys,

The Maximus issue is really quite confusing. With the gconf key set to undecorate, new windows opened should be undecorated and maximised. Can you remove Maximus from your autostart session, run it in a terminal, and paste the output here please. Also, while it's running in the terminal, toggle the undecorate key and please paste the full output from the terminal.

Unfortuantely there are two versions of go-home-applet, one for Dell and one for UNR. The reason for this is that you can drag files/folders/URLs/applications to the go-home-applet, and

1. If your on UNR, they are automatically added to the Favourties section or, 
2. If your on Dell Launcher, you get a popup asking in which category you would like to place the link

Regarding the sneaky "binding" key in Maximus, if you keep it set to Super_L and hit the windows key, you should see that the current window is fullscreened, pressing it again will un-fullscreen it :-).

You can actually make rules using .desktop files so Maxmius sends the right key combination to the current window (so Ctrl+L for Adobe Reader, Ctrl+Shift+J for OO.org). It automatically tries F11 (so Firefox/Totem works out of the box) and finally falls back to just manually fullscreening the window.

Let me know if you like it, I'm planning some blog posts describing UNR in full detail as there are lots of little things people have missed...probably due to the fact that there's no documentation :-)!

Regarding the differences between Dell and UNR, they both use Maximus and Metacity, but the launcher, window picking and go-home-applet differ. The main "theorectical" difference between the two launchers is that the UNR launcher attempts to replace the main-menu on the panel, and the Dell launcher attempts to compliment it.

I hope that clears things up!

---

### Post by DjFIL on 2008-10-18
thanks again for a reply... this is really great to see the friendly help.  here's the results of what i've been able to produce.

maximus is removed from the 'sessions' list. 
gconf-editor for 'maximus' set to:
binding: Super_L
exclude class: [totem,wfica_seamless,ktuberling,gnometris,cheese,kwordquiz]
undecorate: enabled

so in terminal i typed 'maximus', current windows went full screen (still with titlebar) no more text in terminal appeared.

i'm currently viewing my gedit window, which i'm typing this document in.  i pressed windows key, it goes full screen, i lose title bar and my top gnome panel.  following text is given.

** (maximus:5315): DEBUG: Window opened: res_name=Gnome-terminal -- class_name=gnome-terminal
** (maximus:5315): DEBUG: Window opened: res_name=Gedit -- class_name=gedit
** (maximus:5315): DEBUG: Searching rules for djfil@djfil: ~:

** (maximus:5315): DEBUG: 	djfil@djfil: ~ ?= croread
** (maximus:5315): DEBUG: 	NO!

** (maximus:5315): DEBUG: 	djfil@djfil: ~ ?= OpenOffice.org
** (maximus:5315): DEBUG: 	NO!

** (maximus:5315): DEBUG: Sending fullscreen F11 event
** (maximus:5315): DEBUG: Forcing fullscreen wnck event

i pressed windows key to deactivate, all goes back to normal.  folowing text is given.

** (maximus:5315): DEBUG: Sending un-fullscreen F11 event
** (maximus:5315): DEBUG: Forcing un-fullscreen wnck event

i went and viewed terminal, i typed 'maximus' and entered again.  folowing text is given.

** (maximus:5443): WARNING **: Binding 'Super_L' failed!

now while viewing terminal window. i press windows key, same results, i loose the gnome menu and the terminals title bar.  following text is given.

** (maximus:5443): DEBUG: Window opened: res_name=Gnome-terminal -- class_name=gnome-terminal
** (maximus:5443): DEBUG: Window opened: res_name=Gedit -- class_name=gedit

still viewing terminal, i press windows key again, all goes back to normal.  but no new text is provided.

hope this helps... thank you so much for your assistance.

---

### Post by treris on 2008-10-18
I'm glad njpatel has taken an interest in all this, because I sure don't know what the problem is.
Normally I would recommend uninstalling all the packages connected to the netbook remix, but I wouldn't know where to get the dell packages to restore the whole thing afterwards.

Do they come with the normal installation or are they available online somewhere?
I did find a website with links to what seem to be the dell ubuntu repositories for the mini 9. 
[http://www.ubuntumini.com/2008/10/check-out-dells-mini-9-repositories.html](http://www.ubuntumini.com/2008/10/check-out-dells-mini-9-repositories.html)

If these do indeed hold the repositories for the dell mini 9 then maybe you could restore everything.

Do either one of you know whether these are the actual repositories that can create the dell version of the netbook-remix out of a normal hardy installation?

DjFIL, you could check this by looking up the file /etc/apt/sources.list and comparing the contents with the repositories mentioned on that website.

This whole thing might just be caused by a incompatibility between the dell version and the ppa version of the netbook-remix. However unlikely that may seem.

---

### Post by DjFIL on 2008-10-19
yes... those match my sources.list file.  i'm guessing you'd be able to install dell's netbook remix varient using those repositories.  i'm not sure how many files are different, but i can say the maximus file from the canonical netbook remix ppa site is a newer version then that found on dell's site.  and yes, very happy about the assistance i'm getting to get this to work  :)

---

### Post by treris on 2008-10-19
Okay, next thing you could try is to install the dell version of maximus by using 'force version' under the 'package' menu of synaptic (assuming of course that the dell installation includes synaptic..)
It'll give you a warning about going back to an older version and how that's not recommended, but you can ignore that for this time.
Restarting gnome by pressing ctrl-alt-backspace should then do the trick, but you may also reboot and then let's see if that solves the problem. 
I don't really think it will, considering that the dell version is an older version, but it is easy to try so why not.
Of course if it doesn't make a difference feel free to update the maximus package again to the latest version.

I'm glad to 'assist', would be more glad if I could actually solve the problem though.:-?

---

### Post by DjFIL on 2008-10-19
No need to roll back.  After this most recent system restore, when first installing the canonical netbook components, i left the original maximus on the system and only enabled the undecorate option.  it still did the same results, so i then installed the newer maxmius from the canonical netbook-remix ppa's.

---

### Post by njpatel on 2008-10-20
> **DjFIL said:**
> ** (maximus:5315): DEBUG: Window opened: res_name=Gnome-terminal -- class_name=gnome-terminal
** (maximus:5315): DEBUG: Window opened: res_name=Gedit -- class_name=gedit
** (maximus:5315): DEBUG: Searching rules for djfil@djfil: ~:

** (maximus:5315): DEBUG: 	djfil@djfil: ~ ?= croread
** (maximus:5315): DEBUG: 	NO!

** (maximus:5315): DEBUG: 	djfil@djfil: ~ ?= OpenOffice.org
** (maximus:5315): DEBUG: 	NO!

** (maximus:5315): DEBUG: Sending fullscreen F11 event
** (maximus:5315): DEBUG: Forcing fullscreen wnck event

i pressed windows key to deactivate, all goes back to normal.  folowing text is given.

** (maximus:5315): DEBUG: Sending un-fullscreen F11 event
** (maximus:5315): DEBUG: Forcing un-fullscreen wnck event

i went and viewed terminal, i typed 'maximus' and entered again.  folowing text is given.

** (maximus:5443): WARNING **: Binding 'Super_L' failed!

now while viewing terminal window. i press windows key, same results, i loose the gnome menu and the terminals title bar.  following text is given.

** (maximus:5443): DEBUG: Window opened: res_name=Gnome-terminal -- class_name=gnome-terminal
** (maximus:5443): DEBUG: Window opened: res_name=Gedit -- class_name=gedit

still viewing terminal, i press windows key again, all goes back to normal.  but no new text is provided.

hope this helps... thank you so much for your assistance.

Thanks for this. It seems your fullscreening works, but undecoration doesn't :-/. Can you do the same thing, but this time instead of pressing the windows key, toggle the undecorate key in gconf and paste the out put please.

Also, this would be a good time to ask 

1. What window manager are you using (default=metacity) and,
2. Have you modified your exclude_list for maximus?

---

### Post by DjFIL on 2008-10-20
1. What window manager are you using (default=metacity) and,
-i haven't changed this, so it should be metacity.  i see it running in system monitor.

2. Have you modified your exclude_list for maximus?[/QUOTE]
i have not modified the exclude_list.  what i posted is the original contents.

I'm not sure if this is the results you wanted from me testing the undecorate option in gconf editor.  nothing really happened in the terminal window when i actively switched the toggle in gconf-editor for maximus...  so... while maximus' undecorate is still enabled in gconf-editor i type maximus in a new terminal window and get the following...

djfil@djfil:~$ maximus

** (maximus:5301): WARNING **: Binding 'Super_L' failed!

** (maximus:5301): DEBUG: Window opened: res_name=Gconf-editor -- class_name=gconf-editor
** (maximus:5301): DEBUG: Window opened: res_name=Gnome-terminal -- class_name=gnome-terminal
** (maximus:5301): DEBUG: Window opened: res_name=Web Browser -- class_name=Navigator
** (maximus:5301): DEBUG: Window opened: res_name=Gedit -- class_name=gedit

if i disable undecorate in gconf-editor, then close the gconf-editor window, and type maximus on a new line again in terminal i get...

djfil@djfil:~$ maximus

** (maximus:5355): WARNING **: Binding 'Super_L' failed!

** (maximus:5355): DEBUG: Window opened: res_name=Gnome-terminal -- class_name=gnome-terminal
** (maximus:5355): DEBUG: Window opened: res_name=Web Browser -- class_name=Navigator
** (maximus:5355): DEBUG: Window opened: res_name=Gedit -- class_name=gedit

and lastly, if i open gconf-editor, reenable undecorate, close gconf-editor, and type maximus again...

djfil@djfil:~$ maximus

** (maximus:5397): WARNING **: Binding 'Super_L' failed!

** (maximus:5397): DEBUG: Window opened: res_name=Gnome-terminal -- class_name=gnome-terminal
** (maximus:5397): DEBUG: Window opened: res_name=Web Browser -- class_name=Navigator
** (maximus:5397): DEBUG: Window opened: res_name=Gedit -- class_name=gedit

as said, nothing happens in terminal with maximus when actively toggling maxmimus' undecorate on/off.  if there's another way you want me to check this, please specify.  thank you again for further assistance.

---

### Post by LoGraYThS on 2009-05-13
I'm very interested on following this issue.

I have an Acer Aspire One ZG5 (AOA 150) with a fresh install of Jaunty UNR in Classic Desktop Mode.

After fixing a Desktop-Switcher issue as it says [here]("https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519") and looking everywhere in these forums and the interwebs and finally found you guys talking about maximus undecorate feature not working.

I will give follow up to this matter and if need any tests to be made to get an answer I will do it gladly.

Cya 'round!

---


---
title: "Unity greeter wallpaper"
date: 2012-05-03
forum: Desktop Environments
---

### Post by linforlife on 2012-05-03
Hello I was wondering if i could get some help with unity greeter. From what i know you should be able to have your own unique wallpaper for the login. So far i have only changed my desktop wallpaper, i thought that would do the trick. So how do i do it? Still a newbie.....

---

### Post by papibe on 2012-05-03
Hi linforlife.

Check this [article]("http://www.omgubuntu.co.uk/2011/09/tool-change-lightdm-wallpaper-ubuntu-11-10/"). It is for 11.10, but it should work on 12.04 too (both use lightdm).

Hope that helps, and tell us how it goes.
Regards.

---

### Post by Hylas de Niall on 2012-05-03
If you're using 12.04 it *should* display desktop wallpaper at the log-in. Is the image stored somewhere other than in your 'pictures' folder?

---

### Post by linforlife on 2012-05-03
> **papibe said:**
> Hi linforlife.

Check this [article]("http://www.omgubuntu.co.uk/2011/09/tool-change-lightdm-wallpaper-ubuntu-11-10/"). It is for 11.10, but it should work on 12.04 too (both use lightdm).

Hope that helps, and tell us how it goes.
Regards.

Hello I read the article and it didnt help. When I type in the command I get the text editor blank with nothing.

---

### Post by linforlife on 2012-05-03
> **Hylas de Niall said:**
> If you're using 12.04 it *should* display desktop wallpaper at the log-in. Is the image stored somewhere other than in your 'pictures' folder?
my picture is store as follows home/pictures/wallpaper/one.jpg

---

### Post by Hylas de Niall on 2012-05-04
> **linforlife said:**
> my picture is store as follows home/pictures/wallpaper/one.jpg

You could try using one from directly in the pictures folder and see if that works?

---

### Post by Bluenoser81 on 2012-06-01
> **linforlife said:**
> my picture is store as follows home/pictures/wallpaper/one.jpg

Hi, I have been having this problem as well, and I think I figured out what they problem is and how to fix it. I bet you chose to encrypt your home folder didn't you? That is what I did, and I read that LightDM login screen can't access any picture from home/pictures before you log-in because it is still encrypted! After reading this I poked around a bit. I noticed that using the default wallpapers (the ones you see if you chose "Wallpapers" from the "Change Desktop Background" right-click dialog) meant that they would show up on the log-in screen. This is because those default wallpapers are stored in /usr/share/backgrounds/ and aren't encrypted. So that solves the problem why your home pictures folder backgrounds won't show on the log-in screen. Now the fix. 

To fix this we need to put any picture that we want to be able to appear as a login background somewhere *outside *of the home folder (encrypted, remember). I put them in /usr/share/backgrounds along with the default ones. Your changed background should now be on the login screen as well. 

If you look in /usr/share/gnome-background-properties you will see a file called 'precise-wallpapers.xml'. What I did is backup this file first ("sudo cp precise-wallpaper.xml /usr/share/gnome-background-properties/precise-wallpaper-backup.xml") and then "sudo nano precise-wallpaper.xml" to edit it. The file is a simple XML format that points to where backgrounds are stored. Copying the format you could add something like the following (before the </wallpapers> closing tag): 

```

 <wallpaper>
    <name>Beach 4</name>
    <filename>/usr/share/backgrounds/beach4.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

```I added five new ones. The point of doing this is that now when you right-click on the desktop and choose "Change Desktop Background" and "Wallpapers" is selected from the dropdown, you will see the new wallpapers you just added. Alternatively, you *could *simply just keep copying your home/pictures background to usr/share/backgrounds

Take care

---

### Post by deadprotocol on 2012-06-01
This worked for me too.

---

### Post by satish_j on 2012-06-02
For me,the separate wallpaper for login window just flashes and then again displays the desktop wallpaper at login.
I changed the login background after installing ubuntu tweak and selecting one of the default wallpapers(different from desktop wallpaper) for login window.
The new wallpaper for login works,but it just flashes for a second at login window and then switches to desktop wallpaper.
Any ideas how to resolve it?:confused:

---

### Post by Bluenoser81 on 2012-06-02
> **satish_j said:**
> For me,the separate wallpaper for login window just flashes and then again displays the desktop wallpaper at login.
I changed the login background after installing ubuntu tweak and selecting one of the default wallpapers(different from desktop wallpaper) for login window.
The new wallpaper for login works,but it just flashes for a second at login window and then switches to desktop wallpaper.
Any ideas how to resolve it?:confused:

Hmm, not sure about the whole separate login/desktop wallpapers (having 2 different ones). You could try modifying (at your own peril of course) the default value for the login background. Try modifying the values in /etc/lightdm/unity-greeter.conf : 

```
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb
```Just replace background property with the path to the background you want to display. In order to get your desktop background not to overrule the default value in unity-greeter.conf, you will want to have your desktop background stored somewhere where lightdm can't access before login (there may be a simpler solution...anyone?). For me, because lightdm login can't access my home folder before login (encrypted), I could just set my desktop background from my ~/Pictures folder, and the login will always use the default image (warty-final-ubuntu.png from unity-greeter.conf, unless you replace that line). There could be a simpler way, but that should work for you, if you have an encrypted home folder, anyway.

---

### Post by lukejaeger on 2012-12-03
I have the opposite problem: how do I **prevent** users from changing the greeter wallpaper?

We have a bunch of Ubuntu 12 boxes set up as web kiosks in our school library, and they are pretty thoroughly locked down. Any changes a user makes to the desktop environment will be wiped at logout - except, if a user changes their wallpaper, the change persists as the greeter wallpaper!

What file or directory do I have to lock or delete to prevent this?

---

### Post by tomdkat on 2013-01-08
> **Bluenoser81 said:**
> In order to get your desktop background not to overrule the default value in unity-greeter.conf, you will want to have your desktop background stored somewhere where lightdm can't access before loginThanks for posting this.  I did this and I was able to restore my desired configuration of having a separate Unity greeter wallpaper image shown from my desktop wallpaper image.  \\:D/

Thanks!  :)

Peace...

---


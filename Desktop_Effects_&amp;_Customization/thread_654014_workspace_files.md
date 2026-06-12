---
title: "workspace files"
date: 2007-12-30
forum: Desktop Effects &amp; Customization
---

### Post by scottym on 2007-12-30
My other workspacesdo not show the files that are on the first workspace. Is there any way to fix this. I have tried looking at compiz but that freezes the system up. Thanks.

---

### Post by Forlong on 2007-12-30
Are you using Compiz (desktop effects) or not?
And by "files" you mean like icons on the desktop, right?

---

### Post by scottym on 2007-12-31
I had desktop effects enabled but I am not sure that compiz is running. Yes, only one of the fiur desktops has icons on it.  When I run the help command this is the output:

scotty@scotty-laptop:~$ compiz --help
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Usage: /usr/bin/compiz.real [--display DISPLAY] [--bg-image PNG] [--refresh-rate RATE]
       [--fast-filter] [--indirect-rendering] [--loose-binding] [--replace]
       [--sm-disable] [--sm-client-id ID] [--no-detection]
       [--ignore-desktop-hints] [--only-current-screen] [--use-root-window]
       [--version] [--help] [PLUGIN]...

So I am assuming lots of stuff needs to be fixed.

---

### Post by Forlong on 2007-12-31
Post the output of ```
cat ~/.gconf/apps/compiz/general/screen0/options/%gconf.xml
``` and use the forum's CODE tag please (# button)

---

### Post by scottym on 2007-12-31
Output is as follows:

scotty@scotty-laptop:~$ cat ~/.gconf/apps/compiz/general/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="hsize" mtime="1199116738" type="int" value="4">
        </entry>
</gconf>
 
However, after installing the Advanced Desktops Effects interface the icons appeared on the other desktops.

I would really like a work around for using compiz feature with the super key as my IBM laptop has no super key. I tried configuring with the keyboard in preferences but that wouldn't work.

Sorry I don't understand what you mean by code tag # 

BTW your blog is absolutely awesome!

---

### Post by Forlong on 2007-12-31
> **scottym said:**
> after installing the Advanced Desktops Effects interface the icons appeared on the other desktops.
Great. The output looks like it should.
> **scottym said:**
> I would really like a work around for using compiz feature with the super key as my IBM laptop has no super key. I tried configuring with the keyboard in preferences but that wouldn't work.
You have to remap the keybindings in each plugin (I used <Ctrl>+<Alt> or <Ctrl>+<Shift> instead of <Super> for my Thinkpad) or map the Super key to something else, e.g. [Caps Lock](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Using_Caps_Lock_as_Super_L_.28Windows_key.29)
> **scottym said:**
> Sorry I don't understand what you mean by code tag # 
When clicking on "Post Reply" (not the "Quick Reply" feature) there's a toolbar with many icons and one of them looks like this: #

---

### Post by scottym on 2007-12-31
Thanks for all your help.

I tried the ctrl + alt and the shift but it will not work. Nothing appears in the box.

---


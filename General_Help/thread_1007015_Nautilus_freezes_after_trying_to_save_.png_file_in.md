---
title: "Nautilus freezes after trying to save .png file in Inkscape"
date: 2008-12-10
forum: General Help
---

### Post by Saghaulor on 2008-12-10
I installed Inkscape tonight as I need a program that can open an image and can provide clear font rendering.

I tried to save my image as I was nearly finished with it. Inkscape froze and things started going haywire.

The crash in Inkscape may have been due to the fact that I had the same file still open in Gimp.

The real issue however, since Inkscape crashed, Nautilus continues to freeze up every time I try to browse for files. Also, Inkscape crashes when I try to open my .png image that I was adding text to. 

I have since uninstalled Inkscape, and selected reinstall of Nautilus. To no avail however. I've also purged many useless packages that I no longer use, none of which are related, mostly Ubuntu Studio Audio packages. 

I would really like to get Nautilus running normal again, and if possible get Inkscape running properly as well.

Any ideas?

Thank you in advance.

---

### Post by Saghaulor on 2008-12-10
Ps.

If I run Nautilus with sudo privileges, it runs just fine.

It seems something is going kaput when I try to run Nautilus with standard user privileges.

---

### Post by Saghaulor on 2008-12-10
More info.

I've installed pcmanfm, as an alternative to nautilus, hoping that my issue would be resolved.

Unfortunately the issue remains, pcmanfm also crashes when trying to browse. Pcmanfm crashes in sudo mode too, so the issue may be unrelated.

Please help.

---

### Post by Saghaulor on 2008-12-10
bump

---

### Post by Mazin on 2008-12-10
This problem looks mystifying... I assume you restarted your computer already.  What error output (if any) do the programs print to the console?

---

### Post by Saghaulor on 2008-12-10
> **Mazin said:**
> This problem looks mystifying... I assume you restarted your computer already.  What error output (if any) do the programs print to the console?

I will have to try to acquire if and any error output. How do you suggest acquiring said output? Just issuing the program command via console and seeing if anything fishy turns up? Or do programs output run/error logs to a file somewhere?

I'd like to fix this and not have to rebuild. I had just got my laptop running the way I wanted it to and then it pulls this crap. haha.

---

### Post by Mazin on 2008-12-10
Yeah, programs will print whatever diagnostic and debugging output straight to the console window they were run from.  Curiously, nautilus's help says that if you run ```
nautilus -c
``` it will perform self-checks.  It's worth a try, though I doubt that will help much with your case.

---

### Post by Saghaulor on 2008-12-10
Well, nautilus doesn't seem to be saying to much to the console, and yet still freezing up on me when I try to browse.

Here is the console output.

```
stephen@stephen-laptop:~$ nautilus

(nautilus:6132): Gtk-WARNING **: Unable to locate theme engine in module_path: "default",
stephen@stephen-laptop:~$ 
```

I should mention, when I try to explore a folder, it will freeze, then I click the x to shut down the window, after two clicks I'm asked if I would like to wait or force quit, I select force quit. Then nautilus relaunches into the folder I was in when it crashed.

Per your suggestion, I tried the command "nautilus -c", and received the following output. However, nautilus does not seem to load now.

```
stephen@stephen-laptop:~$ nautilus -c
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory

(nautilus:6322): Gtk-WARNING **: Unable to locate theme engine in module_path: "default",
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
stephen@stephen-laptop:~$ nautilus

(nautilus:6326): Gtk-WARNING **: Unable to locate theme engine in module_path: "default",
```

I ran top to see if nautilus was running, indeed it was. So I killed the process and viola, nautilus loads. So I thought I would test whether or not it would open a new directory, and bam, nautilus crashed.

Any new ideas?

---

### Post by Mazin on 2008-12-10
:confused: I'm stumped.  I've never seen any problem like that.  If it's any consolation to you, you can reinstall Ubuntu without losing your home directory, preserving all your settings.  Of course, it could be your settings that cause the problem.  You can test by creating a new user (so that it gets a new home directory) and then running Ubuntu as that user.

---

### Post by Saghaulor on 2008-12-10
Mazin, thanks for all the help.

I was thinking along the same lines, reflecting on the other day when I encountered a corrupted Outlook profile.

I believe something has went haywire in my profile, as running as sudo provides me with normal access, and upon creating a new account, everything seems to be running tip top.

So I guess I'll just have to scrap my profile and start fresh, without a rebuild, thankfully.

I'm still curious to figure out what the hell caused this, but at least for now we have a workaround.

Once again, thank you for the help.

---

### Post by simplemorphic on 2010-01-24
I've had the same problem with .TIF and .JPG files. I haven't tried running in sudo, but I did use the console to remove the file. One one occasion it was the file itself, on the other, it was its containing folder. When I went to cp the file, I got a message stating that it had an incorrect "magic number." Perhaps if one of the elder Ubunts could shed some light on this?

Moreover, would it help if I reinstalled inkscape?

The application 'file browser' is what has been hanging for me. When it does, I lose the ability to click on files, but all of my other commands work just fine. Is this problem do to an inability of Nautilus to process a preview of the file?

Thanks!

---

### Post by Mazin on 2010-01-24
A year later, I don't even remember what I wrote before and have forgotten that I'm still subscribed to this thread.  I assumed it would have been archived by now.

Can you, using the terminal, navigate to the directory containing the problem file and please post the output of
```
ls -l
``` and also run ```
identify problemfile.tif
```?

---


---
title: "GKSudo Question"
date: 2006-08-01
forum: Desktop Environments
---

### Post by LadyDoor on 2006-08-01
I accidentally tried to post this in the HowTo's section...sorry, Moderators. Here's the real posting.

Is there a way to disable the new eyecandyful gksudo effects? Specifically, to disable this business of darkening the rest of the screen and not really letting you access other applications?

Thanks,
Door

---

### Post by exif on 2006-08-01
I think you might be confusing the xgl/compiz UI with gksudo somehow. gksudo is used to give temporary access to reserved commands and files that usually only root has access to. If you're talking about the GUI effects that xgl does (fading all the non-active windows) you get get gset-compiz which is a neat little app will let you configure all the plugins that come with xgl.

---

### Post by Dr. Nick on 2006-08-01
actually I think you get a fade with gksudo even wothout xgl, It was disabled awhile ago but appears to be re enabled now, Ill try and dig up the how to disable it.

---

### Post by Dr. Nick on 2006-08-01
Well the way that apparently worked before doesnt now.

a little reading up reveals the reason they lock the rest of the applications out.

It should stop any other application from accidently or purposefully capturing the input of the password, 


I was thinking of the darkening effect, It was buggy and disabled. Even then though you still could not access other applications.

---

### Post by LadyDoor on 2006-08-01
Oh well...thanks anyway. I guess I'll just start stuff from the console instead. Thanks for your help.

---

### Post by mlind on 2006-08-01
Run gksudo/gksudo with -g (disable-grab) option. Use gksudo --help or man gksudo to see other options
```

gksudo -g *program*

```

---

### Post by Dr. Nick on 2006-08-01
> **mlind said:**
> Run gksudo/gksudo with -g (disable-grab) option. Use gksudo --help or man gksudo to see other options
```

gksudo -g *program*

```


How did you learn this lol. Thats nice, glad you saw it 

Guess I should read the man pages more often, the solution I found on the closed breezy forums had you editing a file that no longer existed to disable the grab.

---

### Post by LadyDoor on 2006-08-01
Awesome! Thanks a lot!

---

### Post by xenon2000 on 2006-08-15
[http://ubuntuforums.org/showthread.php?t=235560&highlight=fade](http://ubuntuforums.org/showthread.php?t=235560&highlight=fade)

I too am trying to disable the fade effect on logout and when the password is asked for. I don't care if all the other windows and apps are not useable. I just don't want the fade effect. The fade effect has nothing to do with security. It can be just as secure without the fade effect.

The command line option -g you mention is great when doing that via xTerm or the console, but useless for the logout button in X or other menu items.

So I am still looking for a solution to this. By the way, I use Xubuntu 6.06 XFce desktop with no XGL Compiz stuff.

---

### Post by mlind on 2006-08-15
> **xenon2000 said:**
> [http://ubuntuforums.org/showthread.php?t=235560&highlight=fade](http://ubuntuforums.org/showthread.php?t=235560&highlight=fade)

I too am trying to disable the fade effect on logout and when the password is asked for. I don't care if all the other windows and apps are not useable. I just don't want the fade effect. The fade effect has nothing to do with security. It can be just as secure without the fade effect.

The command line option -g you mention is great when doing that via xTerm or the console, but useless for the logout button in X or other menu items.

So I am still looking for a solution to this. By the way, I use Xubuntu 6.06 XFce desktop with no XGL Compiz stuff.

For menu items, you can use alternatives for gksu/gksudo. See update-alternatives manual page, and create a launcher that always includes -g parameter.

Do you know the program which is invoked by "Quit.." menu item?

---

### Post by xenon2000 on 2006-08-15
> **mlind said:**
> For menu items, you can use alternatives for gksu/gksudo. See update-alternatives manual page, and create a launcher that always includes -g parameter.

Do you know the program which is invoked by "Quit.." menu item?

I looked at the man page for that as you suggested. But not sure how I need to invoke that command to be globally useful to me. I want to disable the fade effect for the logout and all password prompting windows.

If I have to manually make this change to everything in the menu and do this for ALL my X/Ubuntu installs manually, that is a huge pain. If that is true, I guess I need to figure it out and hope that one day this will have a better solution in Edgy Eft.

---

### Post by mlind on 2006-08-15
> **xenon2000 said:**
> I looked at the man page for that as you suggested. But not sure how I need to invoke that command to be globally useful to me. I want to disable the fade effect for the logout and all password prompting windows.

If I have to manually make this change to everything in the menu and do this for ALL my X/Ubuntu installs manually, that is a huge pain. If that is true, I guess I need to figure it out and hope that one day this will have a better solution in Edgy Eft.

I was thinking of providing a wrapper script for gksu/gksudo using alternatives, but gksu/gksudo doesn't seem to use those in first place.. :(

/edit, ugly hack removed
If anyone wants to run gksu/gksudo without grab, enable /apps/gksu/force-grab gconf key.

---

### Post by xenon2000 on 2006-08-15
I just realized... -g   is --disable-grab

And I thought --disable-grab defeats the security of pausing all applications to prevent possibly grabbing the password as you type or capturing the screen.

If this is so, then -g in unacceptable and the fade effect needs to be controllable by itself as an effect and not just simply disable the event that is tied to the effect.

---

### Post by mlind on 2006-08-15
> **xenon2000 said:**
> I just realized... -g   is --disable-grab

And I thought --disable-grab defeats the security of pausing all applications to prevent possibly grabbing the password as you type or capturing the screen.

If this is so, then -g in unacceptable and the fade effect needs to be controllable by itself as an effect and not just simply disable the event that is tied to the effect.

Yeah :(

I think bugreport should be filed against gksu. I can't find option to disable just the visual effects without disabling grab aswell..

---

### Post by xenon2000 on 2006-08-15
Thanks for all your help. Talking through things like this are helpful to me. I will have to live with the fade effect for now since disabling that level of security is unacceptable for me.

I have another issue I have been trying to resolve. Disabling GDM for text login.

[http://ubuntuforums.org/showthread.php?t=218549](http://ubuntuforums.org/showthread.php?t=218549)

My quote from that thread:

Well, I did this and while it did give me a text login prompt after reboot like I wanted. When I logged in as my normal user and then did

startx

it started my XFce4 desktop and everything looked right. But when I try to do anything that needs the password, it says

Failed to run Services-Admmin
Unable to copy the user's Xauthorization file.

And doesn't work. So I need to get that fixed and still have my disable gdm setup.

=======

If anyone can post more help to that thread or point me to another thread that helps, that would be great. Thanks.

---

### Post by Enigmatic on 2006-08-19
I would be interested in the answers in this thread. I'm also having problems with the Xauthorization file.

---

### Post by xenon2000 on 2006-08-19
> **Enigmatic said:**
> I would be interested in the answers in this thread. I'm also having problems with the Xauthorization file.

I posted a solution in this thread. I forgot that I had been updating 3 different threads. This will be the 2nd thread, not sure  when the 3rd will pop up again. Here is the link.

[http://www.ubuntuforums.org/showthread.php?p=1397955#post1397955](http://www.ubuntuforums.org/showthread.php?p=1397955#post1397955)

---

### Post by mlind on 2006-08-19
You can just delete .Xauthority and restart gdm. That file will be re-created.

If you execute startx as root, .Xauthority gets owned by root..

---

### Post by xenon2000 on 2006-08-19
> **mlind said:**
> You can just delete .Xauthority and restart gdm. That file will be re-created.

If you execute startx as root, .Xauthority gets owned by root..

NOTE: I tried the above in Xubuntu before I did the process I listed. It did not recreate the file for me. Luckily I had renamed and moved it for backup. And when this method didn't work. That is when I tried the permissions method I posted earlier.

Edit: Sorry, restarting GDM will do it... but my solution for the thread I posted originally was to disable GDM and still keep your X session for a text bootup/login, which resulted in Xauthority breaking and I posted the fix for the permissions since you can't just delete and restart GDM if you are trying to disable GDM.

---

### Post by mlind on 2006-08-19
> **xenon2000 said:**
> NOTE: I tried the above in Xubuntu before I did the process I listed. It did not recreate the file for me. Luckily I had renamed and moved it for backup. And when this method didn't work. That is when I tried the permissions method I posted earlier.

Edit: Sorry, restarting GDM will do it... but my solution for the thread I posted originally was to disable GDM and still keep your X session for a text bootup/login, which resulted in Xauthority breaking and I posted the fix for the permissions since you can't just delete and restart GDM if you are trying to disable GDM.

.Xauthority can be created using xauth too. If you've used display cookies, merging a display cookie will create the file is it doesn't exist.

---


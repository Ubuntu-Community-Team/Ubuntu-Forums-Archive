---
title: "how to autostart dropbox (set startup program?)"
date: 2012-06-04
forum: Desktop Environments
---

### Post by idiotprogrammer on 2012-06-04
Hi, there, 

I'm having problems setting up dropbox so that it autostarts. 

First, I am NOT using the Nautilus Drop which you can download the software center. 

The reason is that after doing it I got some error messages about unsupported paths (or something like that). 

So I installed it using the official way [https://www.dropbox.com/install](https://www.dropbox.com/install)

When I run 
~/.dropbox-dist/dropboxd or 
~/.dropbox-dist/dropbox dropbox will start successfully (although the green checkmark icons don't appear in file explorer or in the system tray. But basically everything looks good. 

(by the way, does anyone know what the difference and dropbox and dropboxd is? Which is preferred to run). 

But I don't know the Ubuntu way to add and start an initial service. 

I see top right of window manager has "Startup Applications" but I don't know what to type here and how to test it other than restarting the system. I tried once and it did not seem to work. (The command I typed was "~/.dropbox-dist/dropboxd" which works on my command line but not as a startup. 

I notice that the dropbox URL I gave provided a python script for running dropbox in linux via command line. But this seems like overkill. Does anyone have advice? Thanks.

---

### Post by buzzingrobot on 2012-06-04
My startup application entry for Dropbox is: dropbox start -i

The executable that runs is "/usr/bin/dropbox".  "/usr/bin" is in your PATH.  That's why a full path isn't needed in the startup app.  I suspect "~/.dropbox-dist/dropboxd" would work as a startup entry if you replace the tilde with the full path to your home directory. The startup application does not execute as you, so its Home directory is not your Home directory.

I get the same error message when I try to install Dropbox from the repository, so I install the .deb at Dropbox.  

You should not be having these problem or need to do any of the things you are considering. I'd recommend uninstalling Dropbox, and then install a fresh copy from the Dropbox site.  Let the SoftWare Center install it. After the Software Center says it's done, a small popup appears to lead you through the actual install.  Sometimes it takes a few second before that popup appears.  Click through it and Dropbox should be installed correctly and set to startup automatically.

You can use Dropbox at the command line.  Check the Dropbox site on that. But, since the Dropbox folder perfectly mirrors a real folder, I treat is as a real folder -- in Nautilus and at the command line.

---

### Post by idiotprogrammer on 2012-06-04
First, I believe I read a long thread about why the nautilius-dropbox package was not a good idea. (There was a path error, plus i think it was at the recommendation of dropbox people [https://bugs.launchpad.net/ubuntu/+source/nautilus-dropbox/+bug/909488](https://bugs.launchpad.net/ubuntu/+source/nautilus-dropbox/+bug/909488) ) 

But you solved the immediate obstacle, which was that the startup application assumed you were running it from /usr/bin, so all I had to do was to substitute the tilde for the hardcoded path. Now everything works great. 

By the way, am I correct in assuming that the linux client of dropbox does not have right-click menus from within the file explorer  to revert to previous version (as is true for Windows).

---


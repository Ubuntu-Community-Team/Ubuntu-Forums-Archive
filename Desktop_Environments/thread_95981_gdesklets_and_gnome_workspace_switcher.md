---
title: "gdesklets and gnome workspace switcher"
date: 2005-11-27
forum: Desktop Environments
---

### Post by rockrhino27 on 2005-11-27
Hello all, 

     I recently had a problem a few days ago with gnome's workspace switcher.  The whole thing started from wanting a prettier desktop.  I saw some screen shots in the gallery with people having a launcher on the bottom of their desktop resembling the one in MAC OS X.  I decided to look into how to do this and there are 2 ways.  The more difficult way was hacking gnome to use Englightenment as it's window manager instead of metacity.  The simplier way is installing gdeskets and there is a starterbar desklet which does the job nicely.  

     I decided to go the gdesklets way and see if it satisfies me, and if not attempt the Enlightened Gnome hack.  I installed gdesklets, and before I tried starterbar, I tried gnomebar2.  Gnomebar2 has a workspace switcher builtin to the desklet.  So naturally I removed the workspace switcher I was currently using from a taskbar.  I tried it for a few days and was not satisfied.  I then installed starterbar and I like it a lot better.  

     I just have one problem.  When I tried to put back in place my workspace switcher in the top taskbar, I couldn't get all the workspaces to display.  It would only display the current working desktop.  That is pretty useless.  I found many threads on this forum where other people were having the same problems.  A good one is this:

[http://www.ubuntuforums.org/showthread.php?t=71578](http://www.ubuntuforums.org/showthread.php?t=71578)

There are many others.  The above one didn't solve my problem, but it did help me realize how the schemas work for gnome applets.  Here is how I finally solved the problem.  

For some reason gdesklets gnomebar 2 erased my %gconf.xml file located in /home/<me>/.gconf/schemas/apps/workspace_switcher_applet/%gconf.xml and edited /home/<me>/.gconf/schemas/apps/workspace_switcher_applet/prefs/%gconf.xml .  If you look at the above thread everybody who has this problem gets an error message similar to this:

> Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_10/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_10/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_10/prefs/num_rows' stores a non-schema value

The above error message appears when trying to change the preferences on your workspace switcher that you just placed in your taskbar.  Here is what i did to fix the problem.  

First I created another user on my workstation:
sudo adduser <newuser>
This command will ask you a bunch of questions which will give you a new user.  After this command has completed you will see the new user's files in their home directory.  I then went into terminal, and used the su command to navigate through the files as if I was the new user we just created.  

su <newuser>

Now we are in Terminal, and acting as this new user.  Now we need to find the files before they were altered by gdesklets.  I navigated over to /home/<newuser>/.gconf/schemas/apps/workspace_switcher_applet/prefs/%gconf.xml .  And also home/<newuser>/.gconf/schemas/apps/workspace_switcher_applet/%gconf.xml .  I took these files.  Copied them over to the newuser's home directory.  The commands for that are:

cp %gconf.xml /home/<newuser>/gconf_main.xml
and then again in the /prefs directory:
cp %gconf.xml /home/<newuser>/gconf_prefs.xml

Now that I have them in the home directory for the new user I do not need terminal anymore and can do the rest with a GUI and gedit.  I exited my terminal, got a run prompt and ran the command "gksudo gedit".  That gives me root privledges while using the gedit program.  With that you can open up the gconf xml files in the new user's home directory and save them in your directories.  The only thing is when you save the new files in their respected directories you need to rename them as %gconf.xml and they will be owned by root.  I was unsure how Gnome woud handle the config files owned by root so I decided to change their ownership to my current user.  The following commands from a terminal can accomplish this:

sudo chown currentuser:currentuser /home/<currentuser>/.gconf/schemas/apps/workspace_switcher_applet/%gconf.xml
and
sudo chown currentuser:currentuser /home/<currentuser>/.gconf/schemas/apps/workspace_switcher_applet/prefs/%gconf.xml

After all these steps when I readded the workspace switcher to my taskbar everything worked just fine.  It shows my 4 workspaces and I can graphically switch between all of them with a point and click.  It took me three days to correct this issue.  I could not find a post on this forum that corrected the issue for everybody, because many people have different setups.  I hope this helps.  This is my first attempt writing about how I solved a problem in Linux, so if there are any questions please reply to this thread.  I'll answer as best as I can.  

Thanks, 

Rock

---


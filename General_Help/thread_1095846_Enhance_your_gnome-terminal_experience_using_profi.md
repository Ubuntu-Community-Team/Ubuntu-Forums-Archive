---
title: "Enhance your gnome-terminal experience using profiles"
date: 2009-03-14
forum: General Help
---

### Post by tarantino on 2009-03-14
Gnome terminal supports "profiles", which are collections of settings that affect the behavior and appearance of the terminal. These profiles can be used to greatly enhance your terminal experience.
Creating a new profile

A new profile can be created by navigating to the Edit menu and choosing the Profiles... entry. You can create profile based on one of the existing profiles.
Associating a profile with a command

By default, gnome-terminal starts a shell when creating a new window. However, a profile can be used to configure the command that is launched when the terminal window is created. From the profiles dialog, choose the profile that you want to associate with a different startup command, and choose Edit. In the profile "Editing Profile XXXX" window, navigate to the Title and Command tab. Click the Run a custom command instead of my shell checkbox, and enter your custom command.

I personally use this trick to associate certain profiles with ssh connections to other hosts that I connect to often. I also use the same profile to change my background color so that I can quickly pick out remote sessions from local ones.
Change the icon for each profile

When you have lots of terminal's open, it can be difficult to distinguish between them. The problem is especially bad when you use Alt+Tab to cycle through the windows, but all their icons look the same. Thankfully, gnome-terminal also allows you to associate an icon with each profile. In the "Editing Profile" window, navigate to the General tab, and click on the icon next to Profile icon:. Pick a new icon for your profile. Once the new icon is selected, you will notice that even in Alt+Tab selector windows, gnome-terminals will be shown with the icons associated with their profiles.
Create a panel launcher to launch a terminal window with a particular profile

See this previous tip to learn how to create a custom launcher button on your desktop panel. For the command, use:

gnome-terminal --window-with-profile=NAME

Where NAME, is the name of your profile. Combining this trick with a profile associated with an ssh command gives you a quick "ssh to a host in a gnome-terminal with distinct visual appearance" button.
source:[http://deepdictionary.com](http://deepdictionary.com)

---

### Post by chrisamiller on 2009-03-29
I don't have the profile-icon option in my profile preferences.  What versions of Ubuntu, Gnome, and gnome-terminal are you using?

---


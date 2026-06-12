---
title: "Games - Where are they?"
date: 2005-09-21
forum: Desktop Environments
---

### Post by ngms27 on 2005-09-21
Today I installed several games using the Synaptic Package manager.

However where are they? How do I launch them?

They don't seem to appear in any menu's etc.

PS I'm new to Linux

JonnyT

---

### Post by David Marrs on 2005-09-21
This bugs me about Ubuntu. I'm pretty sure that if I used yum to install an app in Fedora, I could always expect to find that app listed in the applications menu, unless it didn't use the GUI, of course. More often than not, I seem to have to add the app myself in Ubuntu, which just seems like an un-necessary complication to me.

Your best bet is to type the application name at the terminal. Use tab auto-completion to help you find it. Launch the terminal by clicking **Applications->System Tools->Terminal**.

For example, I installed a Lemmings clone called "pingus" recently. "Pingus" is its name so I should be able to run it from the terminal by typing 'pingus' (case-sensitive). Program names are sometimes a little different, however, so you can use tab-autocompletion to improve your chances of finding it. For example, if I type 'pin[TAB]' (ie. I type 'pin' then I hit the TAB key) I get presented with the following:

```
david@ubuntu$ pin[TAB]
ping    ping6   pingus  pinky
david@ubuntu$ pingu[TAB] *(autocompletes to pingus.)*
```

Hit enter and the program will run. You may want to set some options when launching too. For example, I like pingus to run in full-screen mode, so I set the *-f* flag. There are usually many options you can choose from when running an application. To see what they are, type 'pingus --help'.

Once you're happy with your options, it's easiest to add the app to the quick launcher on the top panel:
[list]
[*]Right click the panel -> Add to Panel -> Custom Application Launcher;
[*]Fill in the details as you see fit;
[*]In the **command** field, enter the command you would enter at the terminal. Eg, 'pingus -f --min-cpu-usage'
[*]Find an appropriate icon;
[*]Click OK;
[*]Click the icon to launch the app.
[/list]
You can also install an application from synaptic that enables you to add a launcher to the applications menu (at the moment, the applications menu isn't editable without editing a text file buried somewhere in the system), but I've forgotten what it's called. Thankfully, you'll be able to edit gnome menus natively in Gnome 2.12.

---

### Post by Xiata on 2005-09-21
> **David Marrs]This bugs me about Ubuntu. I'm pretty sure that if I used yum to install an app in Fedora, I could always expect to find that app listed in the applications menu, unless it didn't use the GUI, of course. More often than not, I seem to have to add the app myself in Ubuntu, which just seems like an un-necessary complication to me.

Your best bet is to type the application name at the terminal. Use tab auto-completion to help you find it. Launch the terminal by clicking **Applications->System Tools->Terminal**.

For example, I installed a Lemmings clone called "pingus" recently. "Pingus" is its name so I should be able to run it from the terminal by typing 'pingus' (case-sensitive). Program names are sometimes a little different, however, so you can use tab-autocompletion to improve your chances of finding it. For example, if I type 'pin[TAB]' (ie. I type 'pin' then I hit the TAB key) I get presented with the following:

```
david@ubuntu$ pin[TAB]
ping    ping6   pingus  pinky
david@ubuntu$ pingu[TAB] *(autocompletes to pingus.)*
```

Hit enter and the program will run. You may want to set some options when launching too. For example, I like pingus to run in full-screen mode, so I set the *-f* flag. There are usually many options you can choose from when running an application. To see what they are, type 'pingus --help'.

Once you're happy with your options, it's easiest to add the app to the quick launcher on the top panel:
[list]
[*]Right click the panel -> Add to Panel -> Custom Application Launcher said:**
> Fill in the details as you see fit;
[*]In the **command** field, enter the command you would enter at the terminal. Eg, 'pingus -f --min-cpu-usage'
[*]Find an appropriate icon;
[*]Click OK;
[*]Click the icon to launch the app.
[/list]
You can also install an application from synaptic that enables you to add a launcher to the applications menu (at the moment, the applications menu isn't editable without editing a text file buried somewhere in the system), but I've forgotten what it's called. Thankfully, you'll be able to edit gnome menus natively in Gnome 2.12.

KDE doesn't show gnome games.
gnome doesn't show KDE games.

Plain and simple really. But, of course, VERY inconvenient. Seems that the only reason the KDE links to the gnome applications because they selectively added it into the package. Could be wrong though. Seems to fit the problem though.

---


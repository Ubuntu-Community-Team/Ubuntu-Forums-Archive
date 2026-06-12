---
title: "Executing shell scripts from keyboard shortcut?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by woodythdog on 2006-06-13
I am trying to set up a shell script to execute from a keyboard shortcut and I am not sure why it isnt working (mind you I'm not sure of much as I am a new linux user)

Like many people I am having touble with my ps2 mouse losing synce with the linux box when I switch machines using a KVM.

I have worked around this problem by creating two small script files mouseoff and mouseon

this works but its still a lot of steps to switch machines without the mouse going flaky

I must open terminal type the mouseoff command enter a password then I can switch

I have attempted to create a keyboard shortcut one to turn off the mouse and another to turn it back on by using the Configuartion editor to create a keybinding command to execute the script. I just can't get it to work 

am I missing something simple ??

do I have to somehow call the terminal program and pass the script to it?

Any help would be greatly appreciated!
Thanks
Woody

---

### Post by Ramses de Norre on 2006-06-13
Did you give in the hole path to the script? This is probably necessary, you say you have to give in a password when running it, so you're running it with sudo? That needs to be included in the shortcut command too and you'll need to edit /etc/sudoers to give it run permission without password.
```
export EDITOR=gedit && gksudo visudo
```
And add a line ```
user_name ALL= NOPASSWD: /path/to/script

``` with the correct username and path.
Do this for both scripts.

---

### Post by woodythdog on 2006-06-14
here is the script I am using to turn the mouse off> #!/bin/bash

sudo modprobe -r psmouse

would you mind giving a little more detail on the modificatios you are suggesting I am afraid it whent right over my head......remember i have less tha two weeks experiance as a linux user.

I have placed the scripts in /bin so I don't think the path is an issue?

---

### Post by Ramses de Norre on 2006-06-14
Ok, first of all I'd delete the sudo from the script and put sudo /full/path/to/script as command for the shortcut. 

Next part is to make that you don't need to give in a password, so do following commands: ```
export EDITOR=gedit
``` to set gedit as editor for the next command ```
sudo visudo
``` you're then editing the file that handles sudo priviliges, add a line to the end ```
user_name ALL= NOPASSWD: /path/to/script
``` and fill in your username and the whole path to the script, save, close and try running your script.

If it still doesn't work: give the errors =)

---

### Post by woodythdog on 2006-06-15
That does it!
 I follow your advice and now everthing works just the way i had hoped.

The only additional change I made was adding a line to the mouseon script to turn the mouse off then back on this way if I forget to shut the mouse off before using the kvm I still only need to hit one hotkey to reset the mouse.

Thanks again for your help

---

### Post by dpm on 2006-06-15
I've got exactly the same annoying problem with the KVM switch.

So far my workaround has been to open a shell and type the following:

```
sudo fixmouse
``` 
where *fixmouse* is a simple script in [I]/usr/local/bin:
[/I]```

#!/bin/bash
rmmod psmouse
modprobe psmouse

``` 
but your idea of a keyboard shortcut is a lot better. Thanks for this post.

---

### Post by dpm on 2006-06-15
Just for the sake of completeness, and in case this can help anyone, here's how to associate a keyboard shortcut to the script. Assuming that the script is called *fixmouse* (it could be anything else):

1. Go to **System>Administration>Configuration Editor**.

2. Navigate to **/apps/metacity** (Tip: set a bookmark to this entry, it may become useful in the future)

3. Under **/apps/metacity/****keybinding_commands**, choose a command entry that is not already defined (e.g. **command_1**), double-click it and enter the command to execute:

```
sudo fixmouse
``` 
4. Now go to **/apps/metacity/global_keybindings**, choose the entry corresponding to your command (**run_command_1** in this example), double-click it, and enter the keyboard you want to associate to this acion (i.e. to run the script). I simply give **<Alt>f**.

Now, every time you press <Alt>f, '*sudo fixmouse*' will be executed. Note that you will have to follow the instructions by Ramses de Norre on this thread in order to avoid being asked for a password whenever you run the script.

Cheers.

---

### Post by herkamire on 2007-07-16
I'm dying to execute shell scripts from keyboard shortcuts, but I have no Configuration Editor under System>Administration.

How can I set this up? Do I have to switch window managers or something?

I've got a nice new ubuntu install. I've been using linux for years, but I'm new to ubuntu.

Thanks,   - Jason

---

### Post by herkamire on 2007-07-16
I found a way to execute shell scripts from keyboard shortcuts: install xbindkeys and either xbindkeys-config or write your own ~/.xbindkeysrc file (see "man xbindkeys")

Hope that's useful to people besides me.

Best,   - Jason

---

### Post by dpm on 2007-07-17
> **herkamire said:**
> I'm dying to execute shell scripts from keyboard shortcuts, but I have no Configuration Editor under System>Administration.

How can I set this up? Do I have to switch window managers or something?

I've got a nice new ubuntu install. I've been using linux for years, but I'm new to ubuntu.

Thanks,   - Jason

Try pressing **Alt+F2** and then type

```
gksudo gconf-editor
```in the textbox that appears. This will start the Gnome Configuration editor.

Cheers.

---


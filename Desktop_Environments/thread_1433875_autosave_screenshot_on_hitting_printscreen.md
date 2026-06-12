---
title: "autosave screenshot on hitting printscreen?"
date: 2010-03-19
forum: Desktop Environments
---

### Post by VinisLentoje on 2010-03-19
Hello!

Is there a way to make gnome-screenshot (I think that is what I am using, as it seem to be the default program to take screenshots in gnome, but i am not completely sure), to autosave a screenshot with the current settings every time I hit printscreen? And do it "quietly", i.e. saving the screenshot without any notifications, reporting of the filename, going out of focus of the current window, etc.? And also, automatically naming the file in a way, that no previous files would be overwrited, like, SS-256.png and then SS-257.png and so on?

the current screenshot taking system really unffited to my current needs. The worst thing is being forced to go out of focus of the current window for at least 4 seconds afer hitting the printscreen key to actually save the screenshot. I usually need to take screenshots of the gameplay of various games, and it is sometimes "unfordable" to have 5 seconds or so of inactivity, since that can usually lead into "game over".

Ah, also, I am wondering, if autosaving would be attained, would it be possible to save screenshots in a rapid succession, like 1 screenshot every 1 to 4 seconds? Since currently, that is very hard, if not impossible.

Please share Your thoughts! Thank You!

---

### Post by kaibob on 2010-03-19
I don't know how to do what you want with gnome-screenshot. If you prefer something with a GUI, you may want to look at shutter. I don't use it, but people speak highly of it. 

[http://shutter-project.org/screenshots/](http://shutter-project.org/screenshots/)

An alternative is to use the scrot command line utility, which can be assigned to the PrintScreen key. You could also use the Imagemagick Import utility, but it's slower. 

To try this, install scrot and then enter the following command in a terminal window. The file name is the date and time that the screenshot was taken. It takes a screenshot of the active window, although this is easily changed to take a screenshot of the entire screen by deleted the focus option. There is no notification of any sort that a screenshot has been taken. 

```
scrot --focus --border '%m.%d.%y at %H.%M.%S.png'
```

It's quite easy to write a shell script to take multiple screenshots in succession. For example,

```
#!/bin/bash

for i in {1..10} ; do 
   scrot --border '/home/kaibob/screenshots/%m.%d.%y at %H.%M.%S.png'
   sleep 5
done
```

---

### Post by VinisLentoje on 2010-03-20
Hey!

Thank You for the reply!
I had installed scrot (as I want a non-GUI solution).
It works great, I had customized the line for a filename more suitable for me and to make it move the screenshot to the directory of my liking. For that side, it is just perfect.

But I have a problem. I am only able to run that command in the terminal, but I am unable to bind the command to the printscreen key correctly. On my first try, I had unbound the default bindings of pritsreen key in the key binding configuration program and then make a new binding to the line You wrote me (modified though). It did not work correctly: every time I hit the print key, the window wobbles, and no screenshot is created. Then I tried to create a couple of slightly different bash scripts and make the print key to execute one of them. But nothing (perceivable (as it all must be happening in the background)) happens, e.g. no screenshot. I think, if I could log what happens when I hit that key or there would be some sort of a log saved, I would probably figure out what I am doing wrong by myself, but I guess no such logs or logging possibilities normally exist, due to obvious security reasons.

---

### Post by kaibob on 2010-03-20
> **VinisLentoje said:**
> But I have a problem. I am only able to run that command in the terminal, but I am unable to bind the command to the printscreen key correctly. On my first try, I had unbound the default bindings of pritsreen key in the key binding configuration program and then make a new binding to the line You wrote me (modified though). It did not work correctly: every time I hit the print key, the window wobbles, and no screenshot is created. Then I tried to create a couple of slightly different bash scripts and make the print key to execute one of them. But nothing (perceivable (as it all must be happening in the background)) happens, e.g. no screenshot. 

Before posting, I tested the command-line and script both by entering them in a terminal window and by assigning them to the PrintScreen key, and they both worked fine. If I understand correctly, the command-line and script work for you in a terminal window but not when assigned to the PrintScreen key. Unfortunately, I use metacity and can't help you with key assignments under compiz. Perhaps another forum member can be of assistance. Sorry.

---

### Post by VinisLentoje on 2010-03-20
Thank You for the (quick) reply!

Compiz interferes with the keyboard shortcuts? Hmmm.. Strange.
Ah, and, sorry, I expressed the behavior of the window in a wrong way: the window does not wobble, but sends water ripples, as I replaced the PC Speaker warning signals with the ripple effect, as the sounds are very annoying. So, as I understand, it must be "saying" that the command cannot be executed because of some unknown reason.
The whole "wobble" thing must have given the impression of compiz interfering. Dang, that is an excellent example of what can happen if a person does not think over what he/she wrote at least a couple of times.
Forgot to tell: I used gnome-keybinding-properties to edit the keybindings.
Hope this info will be useful.

---

### Post by kaibob on 2010-03-20
Sorry about the misunderstanding. I use metacity and just don't know anything about Compiz.

I thought I would run through how I did this with metacity; hopefully it will help a little bit. 

I first opened the gconf-editor Configuration Editor and set the following key

```
/apps/metacity/global_keybindings/run_command_1
```

to

```
Print
```

I also set the following key

```
/apps/metacity/keybinding_commands/command_1
```

to

```
scrot --focus --border '%m.%d.%y at %H.%M.%S.png'
```

I then opened the "Keyboard shortcuts" applet and put "Disabled" (no quotes) after "Take a screenshot". 

Now, when I press the PrintScreen key, a screenshot is created in my home directory.

---

### Post by VinisLentoje on 2010-03-21
I did as You said, but still, nothing happens.
I have checked if any other command actually work on that key binding, but they don't, also I tried using another key, but also no effect. I have also checked if changes takes effect. I changed the key combinations to the other commands, and the changes worked.
This behavior is pretty strange. But since it falls out of topic here, I guess I will have to make a new thread dedicated to that (but not before using the search function of course)

P.S. How do I thank a person? (I heard it is possible to thank a person on his/her post, and those thanks are counted or something like that)

---

### Post by kaibob on 2010-03-21
That's a real mystery. As I mentioned, I've been using this for years, and I repeated the whole process just to make sure that I hadn't missed anything. Hopefully someone else will be able to help.

They used to have an option to thank a forum member, and the number of thanks would appear by the forum member's name. They did away with this apparently because it overloaded the forum or something along that line.

---

### Post by Jakey_TheSnake on 2010-03-21
Try going into Compiz Config Settings Manager, then under the "General" options, choose "Commands". Put in your command, change to the key binding tab, press "Grab combo" then press Print Screen. Hope this works ;)

edit: or you could try System > Preferences > Keyboard Shortcuts, then adding your own custom command and assigning it Print Screen. When you assign it print, the default print screen command will be disabled. 

Sometimes, the simpler options are better ;)

---

### Post by VinisLentoje on 2010-03-21
Wow, all I had to do was check the "commands" plugin in compiz's configuration. All the commands I had entered in gconf-editor were there. Thanks! =]
Also, I had actually tried using that "System > Preferences > Keyboard Shortcuts" thingie You suggested as my very first option, as I wrote in my second reply (the fifth post on this thread). But it did not work. Also, I gave witnessed some sort of a strange behavior: when I assigned the key binding to the command and it did not work, I returned the key binding to the default command, but, to my amazement, the default one did not work either. Really strange, huh? 

OK, I have two problems now:

1st: if I bind the command to just the key "Print", it does not work, but if I bind it to something like <Super>Print, then it works. That is quite odd, a single key binding does not work, but a combination does. hmmm.....

2nd: Everytime a screenshot is taken, I see water ripples on the screen, indicating an error. I guess it is because I actually *do* get two errors every time I take one. As I order to execute a program after the screenshot is taken, namely mv command. And make it move the screenshots to a NTFS partition, it complains about being unable to write correct permission configuration. It is quite obvious, since, uhm, NTFS.... Anyway, is there a way to disable warning output in the mv command, i.e. run it in a "silent" mode? I remember many other commands having such possibility. OR to disable the ripple effect just for this event?

---


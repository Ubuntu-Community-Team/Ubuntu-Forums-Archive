---
title: "apply conky script?"
date: 2010-12-27
forum: Desktop Environments
---

### Post by gmenfan83 on 2010-12-27
someone on another website posted a link to a conky script that i liked ....i downloaded it but now how do i go about applying it?

---

### Post by robbiemacg on 2010-12-27
What did you DL, somebody's conkyrc?
Are you currently running Conky? If so, what version are you running and do you know where your conkyrc is located?
If you're running a Conky, your version/system is compatible with the functions called by the new rc, you have all the appropriate fonts, it should be a simple matter of (backing your current rc and) swapping in the new file. You might have to tweak it a bit depending on your display, but it should be pretty straight forward.

Let me know if these questions seem like their coming out of left field. We'll work it out. It's fun to experiment with other people's conkyrc files, build on them as a short cut to getting somewhere cool, break them and learn stuff.

---

### Post by gmenfan83 on 2010-12-27
> **robbiemacg said:**
> What did you DL, somebody's conkyrc?
Are you currently running Conky? If so, what version are you running and do you know where your conkyrc is located?
If you're running a Conky, your version/system is compatible with the functions called by the new rc, you have all the appropriate fonts, it should be a simple matter of (backing your current rc and) swapping in the new file. You might have to tweak it a bit depending on your display, but it should be pretty straight forward.

Let me know if these questions seem like their coming out of left field. We'll work it out. It's fun to experiment with other people's conkyrc files, build on them as a short cut to getting somewhere cool, break them and learn stuff.
ha lol thanks for the tips but yes they are coming out of a japanese notebook to me lol ..i have been using ubuntu for about 3 months and am just now trying to learn the ins and outs of cusomizing my desktops etc ....i do not have conky installed ,should i go to software center a get it?thanks again

---

### Post by robbiemacg on 2010-12-27
That's cool.
Before you get rolling, it might be a good idea to do a little reading ([http://conky.sourceforge.net/](http://conky.sourceforge.net/)) and search the forums if you feel like the FAQ the Conky folks make available is short on details.
You can install Conky using Ubuntu Software Centre. I'd suggest selecting the '**conky-all**' option (see attached screenshot). In this way you'll ensure that you're able to call common functions, etc.
Once you're up and running, you should be able to create a **.conkyrc** file in you Home folder (**~/**).
Depending on the contents of this file you've downloaded, you may find that you need to install fonts or configure system monitors in order to get your display to approximate the one you were admiring, but that work's going to be pretty manageable. You can pose additional questions here or start posting to the always popular [conkyrc thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=post+conky%2A").

---

### Post by gmenfan83 on 2010-12-27
> **robbiemacg said:**
> That's cool.
Before you get rolling, it might be a good idea to do a little reading ([http://conky.sourceforge.net/](http://conky.sourceforge.net/)) and search the forums if you feel like the FAQ the Conky folks make available is short on details.
You can install Conky using Ubuntu Software Centre. I'd suggest selecting the '**conky-all**' option (see attached screenshot). In this way you'll ensure that you're able to call common functions, etc.
Once you're up and running, you should be able to create a **.conkyrc** file in you Home folder (**~/**).
Depending on the contents of this file you've downloaded, you may find that you need to install fonts or configure system monitors in order to get your display to approximate the one you were admiring, but that work's going to be pretty manageable. You can pose additional questions here or start posting to the always popular [conkyrc thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=post+conky%2A").
thank you for you help i downloaded the conky all but it is in usr /share/doc and i have no idea how to apply it ...i also made the folder in home like you said...i went to the wiki but cant seem to find an answer either.....i copied my conky all folder to /home and renamed it .conkyrc and am now searching the thread you gave me

---

### Post by idi0tf0wl on 2010-12-27
You need to replace the contents of your current conkyrc (so to speak, anyway), which will be located one way or another in /etc/conky

The actual conf file will be called .conkyrc (meaning you'll need to "ls -a" to see it) or conky.conf (on a newer Ubuntu installation).

To edit the file, open a terminal (Applcations->Accessories->Terminal) and type:
```
sudo gedit /etc/conky/conky.conf
```
or
```
sudo gedit /etc/conky/.conkyrc
```
Then just replace the contents with the script that you like!

Cheers!

---

### Post by gmenfan83 on 2010-12-27
> **idi0tf0wl said:**
> You need to replace the contents of your current conkyrc (so to speak, anyway), which will be located one way or another in /etc/conky

The actual conf file will be called .conkyrc (meaning you'll need to "ls -a" to see it) or conky.conf (on a newer Ubuntu installation).

To edit the file, open a terminal (Applcations->Accessories->Terminal) and type:
```
sudo gedit /etc/conky/conky.conf
```or
```
sudo gedit /etc/conky/.conkyrc
```Then just replace the contents with the script that you like!

Cheers!
i see i did just that and i got the file script to come up .....now how do i actually use it ?like place them on my desktop etc?

---

### Post by idi0tf0wl on 2010-12-27
run "conky" in a terminal or put it in your start-up scripts so it will start each time you log in. Do you know how to do that?

---

### Post by gmenfan83 on 2010-12-27
> **idi0tf0wl said:**
> run "conky" in a terminal or put it in your start-up scripts so it will start each time you log in. Do you know how to do that?
i ran conky in terminal and this scrrensghot was the output i got.,does this mean the script is more or less incomplete and i have to add to it or finfd someone elses script?also i moved my conky all file to my /home and renamed it .conkyrc...it does not show as a folder anymore but when i type it in terminal it still says its a directory?any suggestions on that?...thank you for all your help it is much appreciated

---

### Post by gmenfan83 on 2010-12-27
here is the screenshot sorry forgot to add it above and and no i dont know how to get conky to be added to start up

---

### Post by idi0tf0wl on 2010-12-27
> **gmenfan83 said:**
> i ran conky in terminal and this scrrensghot was the output i got.,does this mean the script is more or less incomplete and i have to add to it or finfd someone elses script?also i moved my conky all file to my /home and renamed it .conkyrc...it does not show as a folder anymore but when i type it in terminal it still says its a directory?any suggestions on that?...thank you for all your help it is much appreciated

Move it back! Haha. The conky installation put it where it was because that's where it's gonna look for what it's supposed to do. Move it back, rename it to its original name, rinse and repeat and let me know how it works.

---

### Post by gmenfan83 on 2010-12-27
> **idi0tf0wl said:**
> Move it back! Haha. The conky installation put it where it was because that's where it's gonna look for what it's supposed to do. Move it back, rename it to its original name, rinse and repeat and let me know how it works.
ok i still get the same readout..i totally uninstalled then reinstalled  all files would be in the right spot like you said ....then i went to the conky thread and copied someones script to use just for like a test and trial thing to see if i can get it working ...then i opened terminal and typed
sudo gedit /etc/conky/.conkyrc then i pasted the script i got from the thred and saved ,closed it and then opened terminal back up and typed conky and stil got the same readout from the screenshot before....i feel like a moron i just cant get it for some reason!

---

### Post by stinkeye on 2010-12-27
This thread may be helpful to you...
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

### Post by gmenfan83 on 2010-12-27
that seems to be helpful ,thank you for the thread but still whenever i open terminal and type conky i get the error in the screenshot below..even after totally uninstallin /reinstalling and starting over

---

### Post by stinkeye on 2010-12-27
> **gmenfan83 said:**
> that seems to be helpful ,thank you for the thread but still whenever i open terminal and type conky i get the error in the screenshot below..even after totally uninstallin /reinstalling and starting over
Whatever you copied to home folder and renamed .conkyrc isn't a valid conky config.
Delete it.

There is no need to edit /etc/conky/conky.conf

When conky is run it will look in your home folder for a **.conkyrc** file.
If there is no **.conkyrc** it will load the default config at **/etc/conky/conky.conf**

Alternatively you can use the **-c** option to load a specific config.
eg ```
conky -c /path/to/your/config
```

For instance if I download a config from somewhere like [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=1553")
I save it in my **/home/glen/conky** folder as democonky.


Then to run conky with that config I enter in the terminal
```
conky -c /home/glen/conky/democonky
```

If I want to keep it I make a copy and rename it conky1

---

### Post by gmenfan83 on 2010-12-27
> **stinkeye said:**
> Whatever you copied to home folder and renamed .conkyrc isn't a valid conky config.
Delete it.

There is no need to edit /etc/conky/conky.conf

When conky is run it will look in your home folder for a **.conkyrc** file.
If there is no **.conkyrc** it will load the default config at **/etc/conky/conky.conf**

Alternatively you can use the **-c** option to load a specific config.
eg ```
conky -c /path/to/your/config
```For instance if I download a config from somewhere like [**_[COLOR=DarkRed]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=1553")
I save it in my **/home/glen/conky** folder as democonky.


Then to run conky with that config I enter in the terminal
```
conky -c /home/glen/conky/democonky
```If I want to keep it I make a copy and rename it conky1
i would delete the file i created in /home but it does not show ..if i trype in the path in terminalit says its a directory but it does not show in home..any suggestions?

---

### Post by stinkeye on 2010-12-27
> **gmenfan83 said:**
> i would delete the file i created in /home but it does not show ..if i trype in the path in terminalm it says its a directory but it does not show in home..any suggestions?

If a file or folder is preceded with a dot it becomes hidden.
To view hidden files ctrl+h.

---

### Post by gmenfan83 on 2010-12-27
> **stinkeye said:**
> If a file or folder is preceded with a dot it becomes hidden.
To view hidden files ctrl+h.
oh i did not know this obviously ..thanks!

---

### Post by gmenfan83 on 2010-12-27
ok i finally think i got it ...there is a conky showing on my desktop thank you guys very much!

---

### Post by stinkeye on 2010-12-27
You can copy the default config to your home folder so that when you run conky it will load this file.
In the terminal...
```
cp /etc/conky/conky.conf ~/.conkyrc
```

If you run **conky** it will now load this config instead of /etc/conky/conky.conf
Now you can edit **.conkyrc** to your liking.

---

### Post by gmenfan83 on 2010-12-27
> **stinkeye said:**
> You can copy the default config to your home folder so that when you run conky it will load this file.
In the terminal...
```
cp /etc/conky/conky.conf ~/.conkyrc
```If you run **conky** it will now load this config instead of /etc/conky/conky.conf
Now you can edit **.conkyrc** to your liking.
well what would i name the folder that i am copying that to?conky?,,,i am sorry for the possible stupid questions but i have been at this all day and am tired

---

### Post by idi0tf0wl on 2010-12-27
> **gmenfan83 said:**
> well what would i name the folder that i am copying that to?conky?,,,i am sorry for the possible stupid questions but i have been at this all day and am tired

You don't need to name any folder anything. ~ means "home folder" and the / separates directories within the filesystem. If you want to quickly just get it did, run this in a terminal:```
sudo apt-get --purge remove conky
sudo apt-get install conky
```
and then repeat the steps in my original post.

Hope you've stayed pleasant!

---

### Post by stinkeye on 2010-12-27
You don't have to create a folder.
Just run the terminal command.
It will copy /etc/conky/conky.conf your home folder as .conkyrc so that when you you run
conky it will load this file.
As i said before, this is the config file conky looks for.

You should see a basic conky when conky is run.

---

### Post by gmenfan83 on 2010-12-27
> **stinkeye said:**
> You don't have to create a folder.
Just run the terminal command.
It will copy /etc/conky/conky.conf your home folder as .conkyrc so that when you you run
conky it will load this file.
As i said before, this is the config file conky looks for.
when i run 
 /etc/conky/conky.conf 
in terminal i get a permission denied?

---

### Post by gmenfan83 on 2010-12-27
this is the one i have and when i try to change it it just stays the same

---

### Post by gmenfan83 on 2010-12-27
this si what the readout is after i copy and paste the conky script i want then open terminal and type
conky

---

### Post by gmenfan83 on 2010-12-27
let me just say thank you so much to you guys for all your help...im sorry if im being dense but i am trying to understand this

---

### Post by stinkeye on 2010-12-27
I give up.
All yours gmenfan83
](*,)

---

### Post by idi0tf0wl on 2010-12-27
> **idi0tf0wl said:**
> You don't need to name any folder anything. ~ means "home folder" and the / separates directories within the filesystem. If you want to quickly just get it did, run this in a terminal:```
sudo apt-get --purge remove conky
sudo apt-get install conky
```
and then repeat the steps in my original post.

Hope you've stayed pleasant!

Please just do this. If you do, it will work.

---

### Post by gmenfan83 on 2010-12-27
> **idi0tf0wl said:**
> Please just do this. If you do, it will work.
i have and this is what happens and then i go to type conky and i get the same error ....i have done as you say and deleted the hidden files as well ...i just dont underswtand i am doing this as directed

gmenfan83@gmenfan83-Satellite-A205:~$ sudo apt-get --purge remove conky
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  conky*
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
After this operation, 69.6kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
gmenfan83@gmenfan83-Satellite-A205:~$

---

### Post by gmenfan83 on 2010-12-27
and i did eachcommand seperate and after the install command when i type conky i get this

gmenfan83@gmenfan83-Satellite-A205:~$ conky
Conky: /etc/conky/conky.conf: 69: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't open '/sys/bus/i2c/devices/1-002d/temp2_input': No such file or directory
please check your device or remove this var from Conky
Conky: Error destroying thread
Conky: Error destroying thread
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.
gmenfan83@gmenfan83-Satellite-A205:~$

---

### Post by gmenfan83 on 2010-12-27
i finally got it ...i re ran those scripts and finally got it! again thanks so much for all the help and patience ,,,it is much appreciated

---

### Post by idi0tf0wl on 2010-12-27
> **gmenfan83 said:**
> i finally got it ...i re ran those scripts and finally got it! again thanks so much for all the help and patience ,,,it is much appreciated
Glad you got it working! Please do browsersby a favor and mark this thread as [SOLVED].

Here's to hoping you have an awesome everything! Cheers!

---

### Post by robbiemacg on 2010-12-28
Ha! Wow, [gmenfan83]("http://ubuntuforums.org/member.php?u=1196179"), seems like you've learned quite a bit during the hours I was offline! (You've learned about the structure of the file system, picked up some common Terminal commands, figured out quite a bit about Conky too. Awesome.)
You did a great job and managed to keep things positive. Thanks. 

I think trial and error, breaking things and then trying to fix them, is a great way to learn&#8212;particularly when it comes to computers/Linux.
Now that you seem to have the conkyrc you downloaded up and running, you can start getting into some meatier problems if you want to, and learn even more.
Consider cracking that conkyrc open (viewing/editing it with **Gedit** or some similar text editor). Take a look at the file, figure out what parts are rules telling Conky how to display information, and what parts are calling functions and returning info about HDs, CPUs, etc. Change some stuff and see what happens.
Once you start feeling  a little more at home with it, change the conkyrc so that it correctly reflects your own system (and not that of the user who originally posted it), get some of those plugins at the bottom working correctly; watch your Conky run in a Terminal window and figure out what Drives, Libraries, etc. it's looking for and make some changes accordingly. 

There's still more fun to be had working on this project if you're into it.

Good luck!

---

### Post by gmenfan83 on 2010-12-28
> **robbiemacg said:**
> Ha! Wow, [gmenfan83]("http://ubuntuforums.org/member.php?u=1196179"), seems like you've learned quite a bit during the hours I was offline! (You've learned about the structure of the file system, picked up some common Terminal commands, figured out quite a bit about Conky too. Awesome.)
You did a great job and managed to keep things positive. Thanks. 

I think trial and error, breaking things and then trying to fix them, is a great way to learn—particularly when it comes to computers/Linux.
Now that you seem to have the conkyrc you downloaded up and running, you can start getting into some meatier problems if you want to, and learn even more.
Consider cracking that conkyrc open (viewing/editing it with **Gedit** or some similar text editor). Take a look at the file, figure out what parts are rules telling Conky how to display information, and what parts are calling functions and returning info about HDs, CPUs, etc. Change some stuff and see what happens.
Once you start feeling  a little more at home with it, change the conkyrc so that it correctly reflects your own system (and not that of the user who originally posted it), get some of those plugins at the bottom working correctly; watch your Conky run in a Terminal window and figure out what Drives, Libraries, etc. it's looking for and make some changes accordingly. 

There's still more fun to be had working on this project if you're into it.

Good luck!
Thanks....and yes I am into it and that's my next step is to learn how to modify it to my own...I did learn a lot last night trying to get this to work and when I finally did I wanted to kick myself because it was not nearly as complicated as I made it to be but like you said trial and error can be the best ways to.learn(at least for me) and once I have a question about something I must tackle it or die trying ...its just how I am ...and I can't wait to make my own conky script
.thanks to all of you for you help and patience!

---


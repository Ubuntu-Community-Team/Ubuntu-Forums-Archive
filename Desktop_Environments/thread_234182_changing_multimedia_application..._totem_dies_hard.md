---
title: "changing multimedia application... totem dies hard!"
date: 2006-08-11
forum: Desktop Environments
---

### Post by sblanzio on 2006-08-11
Ok, i know that somebody loves totem, but I hate it.

I don't know why, but it seems impossible to me to change the default multimedia reader application to something else.
For example, when I click a .mpg file, then ->properties-> then I click on "Open with" I'm supposed to choose another application, but as I click on another one, anyone it is, my click doesn't produce any result, and "Totem" is still selected.

I know I can choose another software with the right clicking each multimedia file, but I want to open them with mplayer simply doubleclicking them!

So, I decided to uninstall it. and I did

sudo apt-get remove totem

it uninstalled it but something tells me that there's something wrong, since it's keeping opening all the time!!! :evil: 

So, please, how can I seriously uninstall it, and better, how can I successfully change my default multimedia application?

thanks everybody!

sblanzio

---

### Post by louis_nichols on 2006-08-11
Strange thing you're having there. First off, the fact that Totem keeps openning every time you double click a file is by no means its fault. It's nautilus that has a bug there. So, one question about this: after you right click a file and choose another app in the open with dialog, then close the dialog and open it again, is that app stilll selected, or does it jump back to totem? It might be an issue of write rights on the file(s) storing this kind of data.

As for totem starting again... did the apt-get remove command report a succes? No errors? Please post here the output of the command:

```
dpkg -l | grep totem
```

---

### Post by sblanzio on 2006-08-11
> **louis_nichols said:**
> So, one question about this: after you right click a file and choose another app in the open with dialog, then close the dialog and open it again, is that app stilll selected, or does it jump back to totem? 
As for totem starting again... did the apt-get remove command report a succes? No errors? Please post here the output of the command:

```
dpkg -l | grep totem
```


thanks for answering!
well, I should have different options to do that:
1- right click on mpg (or avi) file -> now I can choose "Open with" that means "open just this time with" and I can select Mplayer. It works, but obviously this setting is not saved. I can even choose "Open with another app" and here I can choose another app (even Mplayer again) and it works, but again this setting is not saved. (the next time it comes back totem by default).
2- right click on file and then choose -> properties -> a dialog opens and I choose the "Open with" tab. THis is the point where I get the problem, because I think this should be the right thing to change the default app. I have 4 apps: Caffeine, Totem (that is called something like "Movie player"), Mplayer, and VLC Player. Here Totem is selected but when I try to change this selection clicking on another app, simply nothing happens. I can see the new app highlighted but the selection dot doesn't move! So in fact here I can't choose anything else than Totem!
So, when i doubleclick mediafiles, Totem always starts.

I care to say that the files i'm going to open are owned by my user and the rights are: -rw-r--r--

then, answering your question, this is my output:

```
~$ dpkg -l | grep totem
ii  libtotem-plparser1                     1.4.3-0ubuntu1    Totem Playlist Parser library - runtime vers
ii  totem-gstreamer                        1.4.3-0ubuntu1    A simple media player for the Gnome desktop

```

what could i do?

Thank you for helping!

sblanzio

---

### Post by louis_nichols on 2006-08-11
OK. I think I understand better now. The thing, with the "Open with dialog" is that all settings are stored in a single file, which your user must be able to write to. And, if you say nothing happens when you try choosing another app (I'm guessing the options are also grayed out), it means that quite likely, you can't write to that file. It's not a matter of owning the media files you are trying to play, but that specific file where these settings are written.

Now, I'm not at my Ubuntu box right now and I don't remember the name of this file, but I could tell you later. You could also try searching for it yourself. It's most likely placed in a folder called *.gnome* (yes, with the dot in front) in your home directory and will have a meaningfull name. The contents will be text and not too hard to figure out (syntax is simple most of times). Now, if you do find that file, you should change its attributes so that it belongs to your user and is writable for the owner (i.e. you).

An alternative to this is to simply make all necessary changes to all files and folders in your home dir:
```
sudo chown *user-name* /home/*user-name*/
sudo chmod 700 /home/*user-name*/

```

replace *user-name* with your login name.

Another alternative is to wait till I get home. :)

Now, with the fact that totem is not uninstalled, that's simple. The package totem is what they call a *dummy-package* and its only purpose is to install another package: totem-gstreamer or totem-xine. That's because totem is just a graphical interface. The media files themselves are played by backends, which can be either xine or gstreamer. So the actual totem application on your system is that totem-gstreamer you saw in the list (the command *dpkg -l* lists all installed packages, and *grep* is a filter). You can uninstall that-package if you want...

Hope i was clear enough...

---

### Post by sblanzio on 2006-08-12
thanks for answering!
unluckily i haven't found any file, even hidden files in .gnome or .gnome2 but I have followed this post

[http://www.fedoraforum.org/forum/archive/index.php/t-26875.html](http://www.fedoraforum.org/forum/archive/index.php/t-26875.html)

and it says a complcated way to change the default apps.

the matter, however, is that i'm not going to do all this stuff each time, and so i'm still looking for a solution to my problem!

any idea!?

thanks again

---

### Post by Lofi on 2006-08-14
On a side bar, you sound like you were having the same problems as me. I just moved over from fedora and I wanted Mplayer becuase you can feed it anything. Totem comes with zero codecs and I thought it blew untill I stumbled across this page. 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

so long story short:
hit this page to expand apt-get repos
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

then follow this page 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
with a bunch of sudo apt-get install <paste>

Now I can feed Totem anything and it has a better media manager then mplayer. Or, none of this is close to your problem and I'm wasting time.

---

### Post by sblanzio on 2006-08-14
Thank you for interesting in my problem.

Unluckily my problem is not just about codecs. I got them all. The matter is that I'd like to be able to change my multimedia reader through the file->properties->open with... tab, as everybody does. Instead it seems it's not possible.

I can see all the apps in this tab, and they are not "grey", but as I click them I get no response from the dialog. So it is not possible to change the default reader for each file this way.

I'm forced to do a workaround that is not so easy, and the problem is not just totem (now successfully uninstalled) but just to change the MIME application for each filetypes.

I'm still looking for a solution.

thank you again!

sblanzio

---

### Post by jelly on 2006-08-16
sblanzio, now this may sound like a very silly comment - so I apologize in advance if this isn't your problem.  I just changed my default media player for the first time in Ubuntu, and noticed a usability bug whilst doing so that nearly caught me out - which could be what's happening to you.

In the 'Open With' tab under right-click / properties on a file, you get a list of applications which you can choose.  By default 'Movie Player' or whatever will be selected.  Clicking on the name of the application you want does NOT select it - although it does become highlighted in the list.

You need to click the little dot next to the name of the app you want.

Hope this helps, if not you then someone down the line.  :)

Thanks,

- Jelly.

---

### Post by sblanzio on 2006-08-17
Hi jelly!

thank you very much for your interesting but I already tried to move the little dot. Sometimes it seems that it just moves for a little moment, but it immediately comes back to the "Movie player".

In fact this is not a matter of "movie player", totem, or anything.. this happens with ANY file association. It seems it's impossible to change them through this way. My only chace is to edit the "MIME" config files, and it's very annoying.

I'm thinking that this could happen because I've tried to install several software like "mythtv", "mysql"... and maybe this has broken some link since I know that gnome's filetypes work through a kind of database... but i'm not sure.

So, I'm still looking for a solution. :)

thank you very much again and **don't worry, it wasn't a silly comment! sometimes these little things make the difference**!! :)

byee
sblanzio

---

### Post by gunksta on 2006-08-17
> **louis_nichols said:**
> OK. I think I understand better now. The thing, with the "Open with dialog" is that all settings are stored in a single file, which your user must be able to write to. And, if you say nothing happens when you try choosing another app (I'm guessing the options are also grayed out), it means that quite likely, you can't write to that file. It's not a matter of owning the media files you are trying to play, but that specific file where these settings are written.

Now, I'm not at my Ubuntu box right now and I don't remember the name of this file, but I could tell you later. You could also try searching for it yourself. It's most likely placed in a folder called *.gnome* (yes, with the dot in front) in your home directory and will have a meaningfull name. The contents will be text and not too hard to figure out (syntax is simple most of times). Now, if you do find that file, you should change its attributes so that it belongs to your user and is writable for the owner (i.e. you).

An alternative to this is to simply make all necessary changes to all files and folders in your home dir:
```
sudo chown *user-name* /home/*user-name*/
sudo chmod 700 /home/*user-name*/

``` 
replace *user-name* with your login name.

Another alternative is to wait till I get home. :)

Now, with the fact that totem is not uninstalled, that's simple. The package totem is what they call a *dummy-package* and its only purpose is to install another package: totem-gstreamer or totem-xine. That's because totem is just a graphical interface. The media files themselves are played by backends, which can be either xine or gstreamer. So the actual totem application on your system is that totem-gstreamer you saw in the list (the command *dpkg -l* lists all installed packages, and *grep* is a filter). You can uninstall that-package if you want...

Hope i was clear enough...

I suggest doing this:

```

sudo chown -R *user-name* /home/*user-name*/
chmod -R 700 /home/*user-name*/

```


-R will make these commands function recursively...that is....they will go down ALL of your directories and change everything. And, I could be wrong, but I don't think you will need to use sudo for the chmod here. But, if I'm wrong and you get an error telling you that you don't have permission to do this, use sudo.

--andy

---

### Post by sblanzio on 2006-08-17
> **gunksta said:**
> I suggest doing this:

```

sudo chown -R *user-name* /home/*user-name*/
chmod -R 700 /home/*user-name*/

```


-R will make these commands function recursively...that is....they will go down ALL of your directories and change everything. And, I could be wrong, but I don't think you will need to use sudo for the chmod here. But, if I'm wrong and you get an error telling you that you don't have permission to do this, use sudo.

--andy

Hey man! I owe a beer to you! :) =D> 

that worked perfectly!

how did you know that? what are the files I had to own?

THank you very much!

problem solved! :)

sblanzio

---

### Post by gunksta on 2006-08-18
I took a guess. I saw the idea that luis_nichols posted and I noticed that his idea was lacking the -R, which would make his idea fail to change everything.

All I did was notice a syntax error, he is the one who really figured it out.

--andy

---


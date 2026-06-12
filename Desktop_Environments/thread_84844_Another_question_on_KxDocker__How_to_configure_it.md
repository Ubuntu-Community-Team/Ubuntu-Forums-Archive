---
title: "Another question on KxDocker : How to configure it ?"
date: 2005-11-01
forum: Desktop Environments
---

### Post by TomG on 2005-11-01
Hi 

I set and run KxDocker without problem but I'm unable to manage icons and get the bar that I would like. 
I reviewed official website docs, browsing web and forums and I cant find an understandable method.
I dont understand how the Configurator works (very complex I think).
Should I edit the XML file ? :confused:

Thanks for any tips.
TomG

---

### Post by mxsteini on 2005-11-01
Hm, no you haven't edit the xml-file.
In my systray I found an icon where I can config KxDocker.

There I can configure it.

Michael

---

### Post by TomG on 2005-11-01
Tx for your reply.
Yes I can reach the Configurator from systray icon.
But there are several tabs and I cant find how to add/remove some icons :( 
Tom

---

### Post by kaptainlange on 2005-11-02
Yeah, its pretty confusing, however i should be able to give you a quick run down on how to add icons.

With the configurator window open, make sure you have the objects tab open.  Then on the second row of icons, not the ones on the top, you click the wand looking thing to add a new object.  Once you do that, a default icon will show up at the bottom of the list.  Then you highlight that, then run through the options on the right to modify it.

The images tab will let you set your icon for that object, and the actions icon lets you specify what the command is for the particular object you are making.  You need to know the commands necessary to start a particular program you want to add.

Hope that helps.

Forgot to mention, if you want to delete something, make sure you have the object icon on the left pane highlighted and then click on that black circle with the x in it next to the wand thing.  That should delete it/

---

### Post by TomG on 2005-11-02
Many thanks for explanations. I successfully added my first icon :cool: 
I am/was disturbed by the fact that some apps do not have the same icons in configurator and on the dock (dont know why) so I did not see the link and thought that they not match.
Will try to progress and save my conf file ! ;) 
Tom

---

### Post by Freddy on 2005-11-02
[QUOTE=TomG]Many thanks for explanations. I successfully added my first icon :cool: 
I am/was disturbed by the fact that some apps do not have the same icons in configurator and on the dock (dont know why) so I did not see the link and thought that they not match.
Will try to progress and save my conf file ! ;) 
Tom[/QUOTE]
For certain programs kxdocker already provides icons, go to /usr/share/apps/kxdocker/themes/icons (this on my machine with a compiled 0.39 version using kde-config prefix) and rename the icon to filename_backup.png or just delete it.

Also it fairly importent what group you put the entry in, if you have 2 apps in a group you call "music" only the "higher up" icon will show, roll over the icon and turn the wheel on your mouse for the second app in the music group to appear.

If you don't like that drives and networks that are mounted shows up in the docker, just open up your configurator and change all the entries in "alias" to "disabled"

With time you will get the hang of kxdocker but the configurator is a tricky app but also powerfull.   /// Freddan

Edit: A addon to KaptainLanges little howto, if you don't know the specific command to start the app (it's often the appname itself), you can open up the kmenueditor and look up the app you want to start and check what command to use in kxdockers configurator.

---

### Post by TomG on 2005-11-03
Tx for information.
Tom

---

### Post by Freddy on 2005-11-03
If you have any other questions about kxdocker, like installing plugins or such, just ask.   /// Freddan

---

### Post by TomG on 2005-11-03
My bar starts to be cool ! :cool: :cool: 
May be will come back soon with problems on plugins (clock...) :rolleyes:

---


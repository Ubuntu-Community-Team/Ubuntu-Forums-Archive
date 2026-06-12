---
title: "Using Blender with Platinum Arts Sandbox"
date: 2010-01-04
forum: Gaming &amp; Leisure
---

### Post by myromance123 on 2010-01-04
Hey there, sorry if this is not in the right place.
I don't know where to post this (maybe Multimedia Production ?).

Basically I would like to use Blender to make models and then export them to .md3 meshes so that I can open it in Platinum Art's Sandbox (I really like what you can do with it).

 My only problem is, since I'm using Blender in Ubuntu how do I go about adding the capability of .md3 exporting and importing to Blender?
 I found quite a few how-tos and successful stories of Windows users doing it but...what about Ubuntu or Linux in general? This knowledge would also help me get around to understanding models used in Tremulous.

The Blender site only has .md2 and .md5 (I would also like to know how to get .md5 functionality since the site on Blender.org seems to be as vague as possible on the topic and the other linked site is dead). For .md5s I would like the functionality since I would like to mess around with Blood Frontier's models in Blender.

I know this is probably a very noob or silly way to get into game making for Linux but at least its a start. I'm no pro but I'm starting to understand UV Mapping in Blender and making textures with Gimp and I would like to apply it to something visible. I am able to play around with textures and pre-made models already in Platinum Arts Sandbox but I would like to use some of my own stuff. I'm trying to get a handle on things and would appreciate any help that can be provided.

This site shows how to export to .md3 for use in Sauerbraten, but I don't know what to do with the script provided:
[http://cube.wikispaces.com/MD3+Export+From+Blender+Tutorial]("http://cube.wikispaces.com/MD3+Export+From+Blender+Tutorial")

This forum thread shows how to get .md3 functionality in Windows for Blender for Tremulous models:
[http://tremulous.net/forum/index.php?topic=10571.0]("http://tremulous.net/forum/index.php?topic=10571.0")

This is the site thats suppose to get you up and running with .md5 in Blender but I can't tell if its for Windows users or Linux users are all Blender users in general plus I don't know what to do with the downloaded files:
[http://www.katsbits.com/htm/tools_utilities.htm]("http://www.katsbits.com/htm/tools_utilities.htm")


This is the page from Blender.org that shows other formats it can export and import:
[http://wiki.blender.org/index.php/Extensions:Py/Scripts/Manual/Import]("http://wiki.blender.org/index.php/Extensions:Py/Scripts/Manual/Import")

This forum thread has a script for importing from .md5s but I can't get it to work:
[http://www.doom3world.org/phpbb2/viewtopic.php?t=6901]("http://www.doom3world.org/phpbb2/viewtopic.php?t=6901")

Basically, all the files I downloaded were zipped or archived .py scripts and from what I understand there are two ways to make it run (I think)
 -Opening blender, choosing script mode, shift+F11 and then selecting the script and then Alt+P
 -Copying the .py file and pasting it either in /home/user/.blender/scripts

Both give me errors whenever I try to use them in whatever situation. I either get "Script is not meant to be used that way", "Failed to *something, please check console" and an error I can't remember what it says but it wont let me leave Blender which is why I never tried to recreate it.

As you can see, I did try and find information beforehand. Any help or guidance is seriously needed and appreciated. :)

---

### Post by hessiess on 2010-01-04
Put the script in the .blender/scripts directory and it should automatically show up in the exporter menu, though im not sure exactly where .blender is on Ubuntu (did you install it using APT or download the tar of blender.org?)

You would be better asking on [http://blenderartists.org/forum/](http://blenderartists.org/forum/).

---

### Post by Sindwiller on 2010-01-04
Yeah, but the MD5 importer and exporter scripts from [here]("http://www.katsbits.com/htm/tools_utilities.htm") (there is no guarantee that they'll work with a current version of Blender though since der_ton doesn't update them regularly, not to mention with 2.5 which you shouldn't use anyway as of yet) in *~/.blender/scripts* and both should appear in your File -> Export respectively Import menu.

The [FGD forums]("http://forum.freegamedev.net/") are an appropriate place (they had a crash a while ago, hence why it seems empty :P), otherwise you can just as well ask in the KatsBits forums.

---

### Post by myromance123 on 2010-01-09
I used Ubuntu Software Center to install Blender.
Mmm well I did place the scripts in the right place and they do appear on the menu when I wish to export or import. Problem is it just wont succeed... >.>

 Gives me the previous stated errors. There must be more to importing and exporting than just having the scripts. I asked here first cos I don't have a blender ID for the forum and I also feared no one would answer (noobish question isn't it?).

Thanks for your replies :)

---

### Post by calimer on 2010-01-17
Howdy, Mike here from Platinum Arts Sandbox Free 3D Game Maker.  We have modelers on the team that use blender in linux, so if you are still having trouble, I recommend stopping in to our chatroom sometime and chatting with the modelers.  It might be a good idea in general.
[http://sandboxgamemaker.com/wiki/index.php?title=Contact_The_Team](http://sandboxgamemaker.com/wiki/index.php?title=Contact_The_Team)

Also there have been some major updates especially on the modeling front because we just released a new version of Sandbox, and it includes MovieCube which helps you create Machinima. I'm just mentioning this because you can script commands to give to the model, such as making it walk and then sit and then wave its hand, etc.  The homepage is [http://SandboxGameMaker.com](http://SandboxGameMaker.com)

Take care and good luck!!
-mike

---

### Post by myromance123 on 2010-01-22
Hey sorry no reply for so long, just finished my finals for a trimester.

Thanks Mike for inviting me to your guys chatroom :)

I just fear my questions would hinder your work is all. Maybe if you guys have spare time later on you could put out a little more information in forms of tutorials or videos, then beginners like me wouldn't bother you so much :) (Just an idea, no pressure yeah)

Didn't expect to get a response from one of Platinum Arts Sandbox team members, very cool :P 

 Voted for you guys on moddb, good luck! :D

---

### Post by dmn_clown on 2010-03-03
> **Sindwiller said:**
> Yeah, but the MD5 importer and exporter scripts from [here]("http://www.katsbits.com/htm/tools_utilities.htm") (there is no guarantee that they'll work with a current version of Blender though since der_ton doesn't update them regularly, not to mention with 2.5 which you shouldn't use anyway as of yet) in *~/.blender/scripts* and both should appear in your File -> Export respectively Import menu.

Last I checked the md5 importer Kat was hosting needed to be ran with alt + p from the text editor.  

His exporter was also behind the latest one being hosted by the XreaL project along with instructions on its use [here](http://redmine.xreal-project.net/projects/xreal/wiki/Creating_Player_Models).

---


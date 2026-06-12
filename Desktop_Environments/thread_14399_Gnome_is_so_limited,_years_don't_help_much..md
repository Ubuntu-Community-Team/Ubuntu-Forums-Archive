---
title: "Gnome is so limited, years don't help much."
date: 2005-02-07
forum: Desktop Environments
---

### Post by JoWilly on 2005-02-07
Hi,

Here's the story: a newly installed system, with 2 users. 1 users whats to make a directory with images available to the other user. -> on Gnome it is not possible to do this without a sysadmin (experienced linux/shell user) ? 

Is there no way to change directory permissions so that they apply to all files and subfolders, recursively in Gnome ? If you have a dir full with 500 files, how are you expected to do it ? Change each file manually ?

Fortunately there is the command line -R switch. But how should a new user who doesn't know the shell do this basic thing ?

But why is gnome so limited ? KDE is years ahead (-> this means it will take years for Gnome to catch up... this was the case a few years back, and is still the case today).

I've been coming back to check on Gnome about every 6-12 months during the past years. Everytime as soon as I start to like it I am thrown back the lack of features.

If ubuntu wants to be ready for the desktop soon and not in several years, it should use KDE by default, not Gnome (of course Gnome can still be an option to install for those who like it).

Don't get me wrong. I like Gnome and its look and feel. The problem is that even basic functions are not finished, after all these years.

---

### Post by wulf on 2005-02-07
[QUOTE=JoWilly]Fortunately there is the command line -R switch. But how should a new user who doesn't know the shell do this basic thing ?[/QUOTE]
Learn the shell? If you know enough to be able to say that you need to adjust permissions on a directory, then getting used to the CLI shouldn't really be an insurmountable challenge. I can't comment on how easy or hard the GUI is because I rarely use it for file management but I do feel that the command line is something that shouldn't be hidden in the background; it's a key part of what makes Linux such powerful OS and it isn't all that difficult.

Wulf

---

### Post by Tichondrius on 2005-02-07
[QUOTE=wulf]Learn the shell? If you know enough to be able to say that you need to adjust permissions on a directory, then getting used to the CLI shouldn't really be an insurmountable challenge. I can't comment on how easy or hard the GUI is because I rarely use it for file management but I do feel that the command line is something that shouldn't be hidden in the background; it's a key part of what makes Linux such powerful OS and it isn't all that difficult.

Wulf[/QUOTE]
 
You can easily select all the files in a directory, or a pattern matching a subset of the files, and apply the permission changes to of them. But not sure if you can do it recursively on a directory tree - are you saying you can do this is KDE ?

---

### Post by hashimoto on 2005-02-07
[QUOTE=Tichondrius]You can easily select all the files in a directory, or a pattern matching a subset of the files, and apply the permission changes to of them. But not sure if you can do it recursively on a directory tree - are you saying you can do this is KDE ?[/QUOTE]
 Oh yes, this is one of the things in KDE that Gnome seems to miss: select a folder, change its permissions and everything within the folder gets the same permissions.

Anyway, I found KDE very confusing initially and from me it took quite a long time to grasp it. I "converted" to Gnome with Ubuntu and have not looked back. I just love the pure simplicity of it.

BR
Hashimoto

---

### Post by wulf on 2005-02-07
[QUOTE=hashimoto]Oh yes, this is one of the things in KDE that Gnome seems to miss: select a folder, change its permissions and everything within the folder gets the same permissions.[/QUOTE]
I never used the feature in KDE - as I said, I just learnt how to use the CLI for file management. However, can you change the behaviour in KDE? What if you want to change a folder's permissions but leave the contents untouched? Whichever choice you make with a GUI, there's always going to be someone who wants to go the other way (or you end up with as many options and as much confusion as the command line).

Wulf

---

### Post by Leif on 2005-02-07
While the GUI should be kept simple, adding a little checkbox for "recursively apply" will surely not overclutter it to the point CLI ? I think this would make a useful improvement.

I also don't want to get dragged into the GUI vs CLI debate, but I think the important thing is to give users the choice. Isn't that what linux is about ?

---

### Post by kahping on 2005-02-07
sounds like a feature i would love GNOME to have  :D 

unfortunately, Ubuntu just uses GNOME as it's default desktop environment. the Ubuntu devs are not the same as the GNOME devs, so shouldn't this request be more appropriate if sent to the GNOME devs instead?

kahping

---

### Post by doni on 2005-02-07
hi there...

maybe you should have a look at this [gnome 2.10 preview](http://www.gnome.org/~davyd/gnome-2-10/). there is a nice screenshot about sharing folders....

---

### Post by Dylanby on 2005-02-07
If you look at it from another point of view then this is not a KDE vs Gnome thing.

It's a Konqueror vs Nautilus thing.

You are talking about a feature of Gnome's file manager.

Both KDE (and it's applications) & Gnome (and it's applications) have their strong & weak points.

It's a matter of priorities.

There's only so much time & energy available to the developers of both groups & they have to choose which features, functions, etc they're going to focus their efforts on.

And of course, you can always file a bug against Nautilus for the feature you desire.
I've also read where people have changed the default file manager in Nautilus to something different (although you'll end up with something less integrated).

That's the beauty of Linux, there's so much choice and flexibilty.

One final comment, just MHO but I don't agree that Gnome is "years" behind KDE.

---

### Post by JackDog on 2005-02-07
[QUOTE=wulf]Learn the shell? [/QUOTE]

Ah yes the infamous "backup" argument. Learning the Shell is not an option for an average "user". Gnome prides itself on being more user friendly for average users. But there are serious holes in the DE such as this that prevent it from becoming a desktop for the masses.  Make no mistake by their own admission, Gnome is a "Desktop Environment", not just a window manager. Because of this a Shell should never be needed for everyday tasks. 

I like both KDE and gnome, but KDE is in may respects at least 18 months ahead of gnome (and growing). The only area that I can think of that gnome is beating KDE is vfs (udev/hal/dbsu) support. But with KDE3.4 that will change. 

My parents (and younger siblings) use KDE explicitly because of the limitation that the OP pointed out. Also because of the burning software and konqueror (file browser reasons).  The direction of gnome is both confusing and seemingly futile, I hope that they either change directions or decide a course of development and stick to it. 

I run gnome on my old laptop because its simple and fast. I use KDE for development at work. I feel I have good understanding of both since I actually use them both and not take the word of others.

---

### Post by paul cooke on 2005-02-07
[QUOTE=wulf]I never used the feature in KDE - as I said, I just learnt how to use the CLI for file management. However, can you change the behaviour in KDE? What if you want to change a folder's permissions but leave the contents untouched? Whichever choice you make with a GUI, there's always going to be someone who wants to go the other way (or you end up with as many options and as much confusion as the command line).

Wulf[/QUOTE]

very easily... cos what our OP didn't mention was the presence of a small checkbox in the permission tab of the properties page... 

"Apply all changes to all subfolders and their contents"

check the checkbox and all files and subdirectories in the folder get acted on, uncheck it and only the directory itself, not it's contents gets acted on.

---

### Post by Buffalo Soldier on 2005-02-07
[QUOTE=paul cooke]very easily... cos what our OP didn't mention was the presence of a small checkbox in the permission tab of the properties page... 

"Apply all changes to all subfolders and their contents"

check the checkbox and all files and subdirectories in the folder get acted on, uncheck it and only the directory itself, not it's contents gets acted on.[/QUOTE]
Are you using Warty or Hoary?

---

### Post by JoWilly on 2005-02-07
Hi all,

Thanks to everyone for your replies.

[QUOTE=Buffalo Soldier]Are you using Warty or Hoary?[/QUOTE]

I'm using Hoary, so I can have a good look at the latest features -> this is also why I am disappointed: Gnome 2.10 will be out in 1 month, but today basic features such as recursive directory permissions are still not possible in Gnome.

So maybe the next release, in 7 months ? I've been waiting for years on Gnome, so it won't change me. I am now happy it finally got a decent (but still not yet finished (but we can finally display hidden files !)) open/save file dialog last year, 10 years after OSes like the Amiga had in the early nineties.

> You can easily select all the files in a directory, or a pattern matching a subset of the files, and apply the permission changes to of them.

No you cannot. If you select more than 1 file, the options are greyed out. This is what I tried to do:

1. user1 wants to put 1 directory (he is owner) into the "users" group, with read/write permission, so that all the users in this group can have access.

2. user1 now tries to change the group of the files -> if more than 1 file is selected, user1 cannot change the group...

3. etc...

Anyway, the facts are here: today it is ** NOT POSSIBLE** for a Gnome user to exchange files with another user on the **SAME** computer (he must use the shell for this -> = new user needs sys admin). Can you believe this ?

I have installed this ubuntu machine for someonw who was coming from windows. This person just wanted to make some files available to someone else on the same machine. How could I explain to them this is not possible with Gnome (without selecting 500 files manually (fortunately there are ONLY 500)?

-> I did everything with the shell, but the next time they need to do this, they have to call me and set an appointment with me so that I can do it for them.... forget it.

---

### Post by Tichondrius on 2005-02-07
Yes, I see what you mean... but it shouldn't be hard to fix in the next version (maybe even 2.0).

---

### Post by JoWilly on 2005-02-07
[QUOTE=Tichondrius]Yes, I see what you mean... but it shouldn't be hard to fix in the next version (maybe even 2.0).[/QUOTE]


Yes its a detail... unfortunately its not the only one....  :sad: 

But I think that the reason why many users are sometimes frustrated (as I was again with the above problem), is that many people are spreading the information that Gnome is desktop ready. This is wrong: Gnome is still in development. If this was  explained to new users they would certainly understand it. 

Nevertheless, Gnome has a great future with its HIG, etc... I like the look and feel very much (but good looking and complete icon themes is another story). Thanks a lot to the developpers' hard work.

---

### Post by JackDog on 2005-02-08
[QUOTE=JoWilly]Yes its a detail... unfortunately its not the only one....  :( 
  
 But I think that the reason why many users are sometimes frustrated (as I was again with the above problem), is that many people are spreading the information that Gnome is desktop ready. This is wrong: Gnome is still in development. If this was explained to new users they would certainly understand it. 
  
 Nevertheless, Gnome has a great future with its HIG, etc... I like the look and feel very much (but good looking and complete icon themes is another story). Thanks a lot to the developpers' hard work.[/QUOTE]
  
  You cannot honestly make that argument and feel justified... That is an excuse.
  
 Gnome has been in development since 1997 where it started as a window manager. If 8 years later, it is still not desktop ready, that is pretty sad. If I were a developer, I would bolt. Reason? If a project is that slow or disorganized, its not worth fighting for. Fork it and move on. Gnome isnt desktop ready because they decided not to be. It has some great features and practices that should be followed by other DEs. HIG (as they stand now), spatial nautilus, and a non integrated email/web client are not among them. 
  
 Slackware, HP, RedHat and supposedly Novell/Suse (yeah, I know, evolution, separate discussion) are dropping gnome because of the lack of cooperation and progress in developing a desktop environment for the corporate world. Business is about results, so far gnome is not showing any. For open operating systems to start grabbing desktop market share, businesses have to adopt it first on the desktop. HIG is useless unless all the apps support it which they don't. KDE (KDE app is a different animal than a Qt app) has far better guidelines that programatically have to be followed to develop software in their development frameworks. Since GTK and Gnome are not object oriented, rules can easily be broken and ignored. 
  
 KDE has their own problems, fortunately however they are open to improvements and suggestions. They also utilize their user community instead of dictating. Because of these attributes, KDE is still gaining momentum fast, especially from businesses. Gnome needs to wake up, it has a great potential but as I see it now, they are at least 2 years off. They must beat longhorn out the door with a stable desktop environment or a great blow will be delt to them and more importantly, the OSS community.

---

### Post by ember on 2005-02-08
I think you cannot generally jugde neither KDE nor Gnome that way. It is true that Gnome lacks some features of which you named one and that this is sometimes a very unpleasant experiece. 
Yet the difference to me seems to be more:
KDE - implement features as fast as possible, see to get a solution with clean design later
Gnome - discuss possible solutions first and decide upon what to do afterwards.

This often gives KDE a slight advantage (though I think of months rather than years) - yet since the latest versions of Gnome (2.6 and 2.8) it just feels more productive. Everytime I tried KDE in the last year (several Knoppix and SuSE versions) it was awfully loaded with colours and to me seemed just overloaded with interface configuration options (which made it rather more difficult than easier just to have a normally operating workspace) and I had problemlos to be used only with keyboard available (menus were collapsing as I tried to select programs from the third sublevel).

---

### Post by landotter on 2005-02-08
[QUOTE=JackDog] KDE is still gaining momentum fast, especially from businesses. Gnome needs to wake up, it has a great potential but as I see it now, they are at least 2 years off. They must beat longhorn out the door with a stable desktop environment or a great blow will be delt to them and more importantly, the OSS community.[/QUOTE]

All the business I see around here running desktop Linux run Gnome so I'm not sure what you're talking about. That's not a dig at KDE--just an observation. This is in North America--it may be different in Europe/Suseland... ;P

Gnome is more than ready for the desktop, lets just leave it at that. This need to "compete" against Longhorn is silly 

Could it use a few more features? Certainly--but power users can figure those out now easily enough.

For example: Nautilus is a little austere for major file management. (I like it for day to day stuff, it's simple and elegant) so when you need to run through the directory forest and change a lot of permissions use a better tool like Emelfm, a quintessential two pane file manager (one one of a hundred similar FM proggies).

I would like to see a "recursive" folders check box in Gnome as well.

---

### Post by JackDog on 2005-02-08
[QUOTE=landotter]All the business I see around here running desktop Linux run Gnome so I'm not sure what you're talking about. [/QUOTE]
  
  I see the exact opposite in the US corporate environment.  ;)
  
  My grandmothers and mother use gnome though =)

---

### Post by piedamaro on 2005-02-08
You can't change permissions recursively, but changing permissions on multiple files is working fine since gnome-2.4 (iirc).
Where did you read that RedHat and Novell are dropping gnome?
It seems a bit strange to me after Novell desktop release, which is a gnome-based Suse.

---

### Post by Tichondrius on 2005-02-08
Everything I've been reading suggests that the last Gnome release has been a big hit with users, and that many people prefer it to KDE. It seems like the only people prefering KDE nowadays, are the ones used to using it for a long time, which is understandable, as previously it was much better than Gnome. But Gnome should prove more popular among people just starting to use Linux - that's why Ubuntu chose it as their default DE, and consequently the success of Ubuntu has reinforced Gnome's market share. So if there is a momentum shift, it's certainly not towards KDE right now.

---

### Post by Domhnull on 2005-02-08
I'm still a new linux user.  I tried a variety of distros before settling on Ubuntu - but one of the reasons was its ties with Gnome.  After everything that I had read and tried out I ended up liking Gnome better.  I still do.  I rarely use Windows anymore except at work - but when I do I miss Gnome.  KDE is fine but Gnome works better for me.  I think it's great that we have so many choices under Linux.  If I wanted a KDE-focused distro that's what I'd still have installed.

---

### Post by JoWilly on 2005-02-08
[QUOTE=piedamaro]You can't change permissions recursively, but changing permissions on multiple files is working fine since gnome-2.4 (iirc).
[/QUOTE]

Yes you can select several files at once, and change the perms, but you cannot change the group.

When several files are selected, the group change is not available... go figure why...

What I wanted to do is put a complete directory with files into the "users" group, so that all users in this group have read/write access. -> The only way to do this in gnome is to select one file after the other, manually...

---

### Post by ralph_ubuntu on 2005-02-08
[QUOTE=JoWilly]Yes you can select several files at once, and change the perms, but you cannot change the group.

When several files are selected, the group change is not available... go figure why...

What I wanted to do is put a complete directory with files into the "users" group, so that all users in this group have read/write access. -> The only way to do this in gnome is to select one file after the other, manually...[/QUOTE]
 or simply use an other filemanager than nautlius.
Easy, isn`t it?

---

### Post by JsPr on 2005-02-08
...like gentoo :-) (the file manager not the distro)

---

### Post by paul cooke on 2005-02-08
[QUOTE=JsPr]...like gentoo :-) (the file manager not the distro)[/QUOTE]

or Konqueror.... grins, ducks and runs...  :rolleyes: 

you don't HAVE to use the KDE desktop to take advantage of KDE programs... you can run them very easily in Gnome as long as you've got enough of KDE installed... no-one's behind you holding your arm in a half-Nelson forcing you to use KDE while running KDE programs.

 8-)

---

### Post by JoWilly on 2005-02-08
[QUOTE=ralph_ubuntu]or simply use an other filemanager than nautlius.
Easy, isn`t it?[/QUOTE]


Yes.... I did it with the shell..., but this was not what this post was about.

The story was that a new user needs a sysadmin/experienced linux user, to do this if he uses Gnome...    in KDE the new user can just select "do it recursively", and group selection also works.

---

### Post by Ironi on 2005-02-08
> **Tichondrius]Everything I've been reading suggests that the last Gnome release has been a big hit with users, and that many people prefer it to KDE.
 [/QUOTE]
 Links?
 
 > 
 It seems like the only people prefering KDE nowadays, are the ones used to using it for a long time
 
 Well, I have used it for a while, and I stick with it because I like it and because it doesn't insult my intelligence by removing useful features and options every other release. Long ago, I used to like GNOME (back in the 1.x days) said:**
> 
 as previously it was much better than Gnome.
 
 "Previously," eh? What makes GNOME better than or even as good as KDE? Provide plenty of **technical** (not aesthetic) reasons why you believe this is so... Good luck with that. ;)
 
 > 
 the success of Ubuntu has reinforced Gnome's market share.
 
 Oh? What about people like me who switched to Ubuntu and still use KDE? Have you determined that, say, 90% of Ubuntu users are using GNOME? Where are the numbers to back this up? :p
 
 > So if there is a momentum shift, it's certainly not towards KDE right now.
 How can you be so sure?

---

### Post by JoWilly on 2005-02-08
+krusad[QUOTE=JsPr]...like gentoo :-) (the file manager not the distro)[/QUOTE]

Yes... I have used gentoo in the past until I discovered krusader, for several years. it's excellent, but not developped anymore.

IMHO krusader is the best file manager available in Linux, if you want to get work done. I still cannot understand how work can be done in IExplorer like file managers; its so much faster to copy/move/etc... files from 1 place to the other with a 2 panes setup. Nautilus is just nice if I want to have a look at pictures, or such...

Gnome-commander is dead. I hope tuxcommander will catch up soon.

---

### Post by JackDog on 2005-02-08
[QUOTE=Tichondrius]So if there is a momentum shift, it's certainly not towards KDE right now.[/QUOTE]
 
 Hehe yeah right. Did you hear about Qt4 wrt Windows? KDE just got a huge lift, think about it =)   Do you know what object oriented design patterns are? Or how about the unified db connector in Qt4? shared ioslaves? Can you change the color of your gnome theme through the pref manager?  Which web engine did Apple use? Want to see a real HIG that all apps programmatically _have to_ to support? 
 
 Gnome users are a different type of user. This isnt like the KDE2 Gnome1 days where both were fairly similiar (mainly due to the lack of features). Gnome is built for an average computer user like your mom. KDE is built for power users like a developer, although they seem to think sometimes average users like it too. If you havent _used_ KDE you have no room to talk. I use KDE daily for 9 hours and Gnome at home for 2-3 hours a night on my laptop.  If you havent _used_ both, not just installed it, you have absolutely no room to talk. The default KDE install is outright fugly (in my little opinion). So is the selection method in konqueror. My KDE is setup so its looks just like a Mac (within reason). usability wise its like a cross between windows and a mac.  I should attach my kderc's and you would see what KDE can look and act like.
 
 They are both very good desktop environments, but they definitely have their limitations. Gnome believes the user should be coddled and advanced options should be hidden. That is all good and fine, like I said, my mom loves it... KDE believes all the options with help documents should be shown. Lets the users decide what the hell they want to do. They leave it up to the administrators and distributions to decide which options to allow the user to see. KDE setup correctly, can show just as few options as gnome does. 
 
 To each his own.

---

### Post by ensiferum on 2005-02-08
Yes, nautilius is limited. And even worse than that it's way too buggy, and working with files with both nautilus and CLI tools results in frequent crashes. Yay!

I only use it at the moment for the MIME information, but as soon as I find something that that works properly in that regard nautilius is history for me. It's a shame actually, that Gnome project is clinging onto nautilus so badly. It doesn't stand up with rest of the Gnome DE.

---

### Post by ralph_ubuntu on 2005-02-08
[QUOTE=JoWilly]Yes.... I did it with the shell..., but this was not what this post was about.

The story was that a new user needs a sysadmin/experienced linux user, to do this if he uses Gnome...    in KDE the new user can just select "do it recursively", and group selection also works.[/QUOTE]
 I didn't even mention the shell.

The point is, though I agree with you that this functionality would certainly be useful in nautilus, it's absence doesn't mean that gnome is unusable or you have to be a sysadmin to do it, you simply have to use an other filemanager for the job. And again, that's a pretty easy solution, isn't it?

---

### Post by Tichondrius on 2005-02-08
[QUOTE=JackDog]Hehe yeah right. Did you hear about Qt4 wrt Windows? KDE just got a huge lift, think about it =)   Do you know what object oriented design patterns are? Or how about the unified db connector in Qt4? shared ioslaves? Can you change the color of your gnome theme through the pref manager?  Which web engine did Apple use? Want to see a real HIG that all apps programmatically _have to_ to support? 
 
 Gnome users are a different type of user. This isnt like the KDE2 Gnome1 days where both were fairly similiar (mainly due to the lack of features). Gnome is built for an average computer user like your mom. KDE is built for power users like a developer, although they seem to think sometimes average users like it too. If you havent _used_ KDE you have no room to talk. I use KDE daily for 9 hours and Gnome at home for 2-3 hours a night on my laptop.  If you havent _used_ both, not just installed it, you have absolutely no room to talk. The default KDE install is outright fugly (in my little opinion). So is the selection method in konqueror. My KDE is setup so its looks just like a Mac (within reason). usability wise its like a cross between windows and a mac.  I should attach my kderc's and you would see what KDE can look and act like.
 
 They are both very good desktop environments, but they definitely have their limitations. Gnome believes the user should be coddled and advanced options should be hidden. That is all good and fine, like I said, my mom loves it... KDE believes all the options with help documents should be shown. Lets the users decide what the hell they want to do. They leave it up to the administrators and distributions to decide which options to allow the user to see. KDE setup correctly, can show just as few options as gnome does. 
 
 To each his own.[/QUOTE]


Look, it's just a desktop environment - it's supposed to make it simple to organize and launch your apps and access your documents, as well as provide a visually pleasing interface, which is clear and easy to control. I'm sure that if you spend enough time with KDE, it would become easier to manipulate, but even so I don't see any advantage it will have over Gnome. Anyway, I use the CLI quite a lot for many complex tasks, which would be too complex and time consuming to do using a GUI, no matter how many options it might have. I still think that in the end, for the tasks I do use the desktop environment for, I can perform them faster (less clicks) and simpler with Gnome.

---

### Post by JoWilly on 2005-02-08
[QUOTE=ralph_ubuntu]
The point is, though I agree with you that this functionality would certainly be useful in nautilus, it's absence doesn't mean that gnome is unusable or you have to be a sysadmin to do it, you simply have to use an other filemanager for the job. And again, that's a pretty easy solution, isn't it?[/QUOTE]

Easy for you yes, what about the new user (as I said I have installed the system for a new user)?

The problem is that unfortunately, this is only one example... there are many. If you are used to KDE, features are missing. Something that was easy and fast to do with KDE suddenly cannot be done in Gnome, or is complicated to do because Gnome does not have the feature.

There are many examples. The last one I heard about yesterday, is that Gnome 2.10 will not have a menu editing dialog.... no way to edit menus in Gnome 2.10 (appart from editing .desktop files manually). Gnome developers have once again suddenly decided that their code was not good enough, and have dropped the feature (last time they did this was with Gnome 2. Gnome 1 was full of features, and suddenly we were left with ZERO features). Hopefully menu editing will be back in the next Gnome (2.12 or 3), in 7 months.... ?

As I said, Gnome is not finished, its in development and will catch up (it finally got a 3/4 finished open/save file dialog last year.... it just takes time).

But while Gnome is trying to catch up, KDE is improving... I am now talking about Gnome 2.9 in Hoary (which will be final in 1 month) -> this can only be compared to KDE 3.4 (beta2 is coming out within days).

---

### Post by ember on 2005-02-08
[QUOTE=JoWilly]
The problem is that unfortunately, this is only one example... there are many. If you are used to KDE, features are missing. Something that was easy and fast to do with KDE suddenly cannot be done in Gnome, or is complicated to do because Gnome does not have the feature.
[/QUOTE]

Are you sure that things are not just done different? ... when I started with Linux a few years ago, I often thought important features were missing (and some actually did), yet Linux worked just another way than Windows. 
When it comes to KDE, I feel it's similar. If I'm confronted with a KDE desktop I have to look where Options might be quite long whereas I'm just used to Gnome. But that does not mean KDE lacks that features.

[QUOTE=JoWilly]
There are many examples. The last one I heard about yesterday, is that Gnome 2.10 will not have a menu editing dialog.... no way to edit menus in Gnome 2.10 (appart from editing .desktop files manually). Gnome developers have once again suddenly decided that their code was not good enough, and have dropped the feature (last time they did this was with Gnome 2. Gnome 1 was full of features, and suddenly we were left with ZERO features). Hopefully menu editing will be back in the next Gnome (2.12 or 3), in 7 months.... ?
[/QUOTE]

As far as I know it will be in Gnome 2.10 - yet maybe your information is newer.

But I think of greater importance than the features of the desktop enviroment is the integration of applications. At the moment it is now too easy (unless you like bluecurve) to have a relatively seamless integration of KDE-apps in Gnome and vice versa. So if you do like Gnome and GTK-Applications better than the QT-parts it'll be likely that you favour Gnome, rather not for the DEs features but for the presentation of a consitent workspace.

---

### Post by Tichondrius on 2005-02-08
[QUOTE=ember]Are you sure that things are not just done different? ... when I started with Linux a few years ago, I often thought important features were missing (and some actually did), yet Linux worked just another way than Windows. 
When it comes to KDE, I feel it's similar. If I'm confronted with a KDE desktop I have to look where Options might be quite long whereas I'm just used to Gnome. But that does not mean KDE lacks that features.



As far as I know it will be in Gnome 2.10 - yet maybe your information is newer.

But I think of greater importance than the features of the desktop enviroment is the integration of applications. At the moment it is now too easy (unless you like bluecurve) to have a relatively seamless integration of KDE-apps in Gnome and vice versa. So if you do like Gnome and GTK-Applications better than the QT-parts it'll be likely that you favour Gnome, rather not for the DEs features but for the presentation of a consitent workspace.[/QUOTE]
 If Gnome really does suddenly disallow menu editing in the new version, it will be a major limitation. I don't know why would they do something like that on purpose.

---

### Post by miho on 2005-02-08
[QUOTE=Tichondrius]Everything I've been reading suggests that the last Gnome release has been a big hit with users, and that many people prefer it to KDE. It seems like the only people prefering KDE nowadays, are the ones used to using it for a long time, which is understandable, as previously it was much better than Gnome. But Gnome should prove more popular among people just starting to use Linux - that's why Ubuntu chose it as their default DE, and consequently the success of Ubuntu has reinforced Gnome's market share. So if there is a momentum shift, it's certainly not towards KDE right now.[/QUOTE]
apt-update kde =D>

---

### Post by AndersAA on 2005-02-08
about menu updating in gnome... it will be there, of course they are not gonna turn that off.  It's broke in the current test versions because of some changes to get that system to work better, dont worry, they'll get it working for final.

---

### Post by JoWilly on 2005-02-08
[QUOTE=ember]Are you sure that things are not just done different? ... when I started with Linux a few years ago, I often thought important features were missing (and some actually did), yet Linux worked just another way than Windows. 
When it comes to KDE, I feel it's similar. If I'm confronted with a KDE desktop I have to look where Options might be quite long whereas I'm just used to Gnome. But that does not mean KDE lacks that features.[/QUOTE]

You have a good point.

But KDE is nevertheless ahead with features (now some users may take it as a disadvantage as they find themselves confused).

Anyway, both desktops are great (I like them both). This is the advantage Linux has over Windows: there is choice for everyone.

---

### Post by JoWilly on 2005-02-08
[QUOTE=AndersAA]about menu updating in gnome... it will be there, of course they are not gonna turn that off.  It's broke in the current test versions because of some changes to get that system to work better, dont worry, they'll get it working for final.[/QUOTE]

If this is true, its excellent news.

The information I had was from an Ubuntu developper, here on another thread. He said Gnome has changed the menu handling to be freedesktop.org compliant. Therefore menu editing would not be available in 2.10 as there was no GUI for it now, and as the release is in 1 month there is no time to make one.

But if you got your information from a closer source, thats great news.

---

### Post by macewan on 2005-02-08
[http://www.gnome.org/~davyd/gnome-2-10/](http://www.gnome.org/~davyd/gnome-2-10/)

looks really nice

---

### Post by Chris Ferrell on 2005-02-16
[QUOTE=JackDog]You cannot honestly make that argument and feel justified... That is an excuse.
  
 Gnome has been in development since 1997 where it started as a window manager. If 8 years later, it is still not desktop ready, that is pretty sad. If I were a developer, I would bolt. Reason? If a project is that slow or disorganized, its not worth fighting for. Fork it and move on. Gnome isnt desktop ready because they decided not to be. It has some great features and practices that should be followed by other DEs. HIG (as they stand now), spatial nautilus, and a non integrated email/web client are not among them. 
  
 Slackware, HP, RedHat and supposedly Novell/Suse (yeah, I know, evolution, separate discussion) are dropping gnome because of the lack of cooperation and progress in developing a desktop environment for the corporate world[/QUOTE]


You are very misinformed about many things.

First of all, RedHat and Novell are firmly committed to Gnome.  Everyone knows that RedHat will never drop Gnome and Novell just bought Ximian (a Gnome shop) and the head of desktop development is Nat Friedman. Sun is firmly committed to Gnome and is a huge contributor to Gnome as huge Linux vendor.

All of the momentum is going towards Gnome.  Just look at freedesktop.org and read some mailinglists.

I've always thought that KDE was technically superior,  but now that Gnome has D-Bus/HAL that lead is shrinking.

Some things that people don't seem to realize is that KDE can never be the corporate desktop standard because of it's reliance on QT.  Why do you think RedHat and Sun chose Gnome?

---

### Post by Ironi on 2005-02-17
[QUOTE=Chris Ferrell]
  All of the momentum is going towards Gnome. Just look at freedesktop.org and read some mailinglists.
  [/QUOTE]
  I fail to see how just looking at [freedesktop.org]("http://freedesktop.org/")  and reading "some mailinglists" (which?) proves that "all of the momentum is going towards GNOME."
  
  > 
  I've always thought that KDE was technically superior
  
  Great, me too -- and I still think so.
  
  > 
  but now that Gnome has D-Bus/HAL that lead is shrinking.
  
 Not a chance. From my perspective, GNOME is actually losing ground when it comes to technical merits. The addition of hal and dbus, even if they were intended for GNOME only, does little to change that.
  
  > 
 Some things that people don't seem to realize is that KDE can never be the corporate desktop standard because of it's reliance on QT.
  
  Oh? Why, then, does [this site]("http://enterprise.kde.org/") exist?

---

### Post by Chris Ferrell on 2005-02-17
Ironi

It's RedHat, Novell, and Sun.  The 3 big players are all Gnome.  

Random sites that say "Enterprise KDE" really doesn't mean much, as you should know.

It's common knowledge that until the QT license goes LGPL or BSD or some other less restrictive license than KDE can never be the "standard" desktop.  

Once again, since we'll agree that KDE is technically superior, why do you think that RedHat, Sun, and Novell now all went Gnome?

And it's hard to take JackDog seriously when he's claiming that RedHat and Novell are dropping Gnome.

---

### Post by Ironi on 2005-02-17
[QUOTE=Chris Ferrell]It's RedHat, Novell, and Sun.  The 3 big players are all Gnome.  
 [/QUOTE]
 As an individual Ubuntu desktop user, I should care because...?
 
 > 
 Random sites that say "Enterprise KDE" really doesn't mean much, as you should know.
 
 That site just proves that some businesses do, indeed, use KDE on the corporate desktop. IANAL, so I don't know whether or not QT requires them to pay TrollTech for licenses. Do you know?
 
 > 
It's common knowledge that until the QT license goes LGPL or BSD or some other less restrictive license than KDE can never be the "standard" desktop. 
 
 Again, IANAL. Are you claiming to be one? I've never heard of such "common knowledge," so perhaps you could provide links from authorative sources? It should be quite easy to prove if it's as common as you say, right?
 
 > 
Once again, since we'll agree that KDE is technically superior, why do you think that RedHat, Sun, and Novell now all went Gnome?
 
 I don't know -- perhaps because GNOME is a better fit for users that aren't so technically inclined as, say, myself? History has shown several times that technical superiority does not guarantee victory over lesser competition (see also: Beta vs. VHS, Alpha vs. x86, et. al.). GNOME also seems to please usability afficiandos (to put it mildly).

---

### Post by Tichondrius on 2005-02-18
in what way is kde supposedly "superior" ? that it has more configuration options, or that it has translucent backgrounds which just make things more cluttered ? what I want to konw is why none of the desktop environments lets you suspend and resume apps using the  GUI, which is a feature linux kernel supports ?

---

### Post by Poldi on 2005-02-18
ok. a lot has been said by others better than I could have but this:

[QUOTE=JackDog]
...
It has some great features and practices that should be followed by other DEs. HIG (as they stand now), spatial nautilus, and a non integrated email/web client are not among them. 
...
[/QUOTE]

does prove (at least for me) that we won't find a common ground here and what we are looking for in a desktop are so completely different things that it is good we have the choice.

the three features you mentioned are the three top features that make me like Gnome over KDE. now how could we ever get a desktop we both like?

I think this among other point shows the limits of a 'diverge towards common ground strategy', the limits of building a common desktop that takes the 'best' parts of each Gnome and KDE and to some degree the llimits of mixing components from the different camps.

if I as a Gnome uses name the HIG, spatial nautilus and a strict seperation of filebrowser and webbrowser/collaboration software as the prime features why I use Gnome and you as a KDE user the same features as the prime issues from top of your head that make Gnome inferior then how are we (or others) ever to agree upon what a 'perfect' desktop would like?

I see another indication for my claim that what some are arguing about as 'better or not' is only a matter of taste or intentionally different ways to work with the system:

just take a look the theming sites for Linux: art.gnome.org, kde-look,org, gnome.look.org, customize.org etc.

have you ever wondered why, given the sheer mass of themes available, extremely few top-KDE themes have been rebuild for Gtk/Gnome and extremely few top-Gnome-themes have been for KDE? there are exceptions of course - Plastic, Crystal, Blucurve and Industrial are somewhat popular both sides of the border, but what I see mostly is that there is a distinctive style to KDE desktops as there is for Gnome desktops. it is not that there is no copying going one in the theming department - Win XP and Mac looks are getting ripped all the time but who uses a 'SmoothGnome' or UserLinux' 'Office' alike on KDE?

looking beyond theming I see the same regarding the 'feel' of the desktop. both usergroups could do a lot to make Gnome feel as much like KDE or KDE as much like Gnome as possible but I don't see it happen. I could switch spatial browsing off and use GConf to make as much default choices 'KDE-alike' but I and most other just don't. instead most users I know emphasise the differences than make their desktops distinct.

for me, the way Gnome became in 2.6 and the direction it is heading ever since was the reason that made me switch to Linux completely.

kind regards,
Carsten

---

### Post by rkn on 2005-02-18
Getting back to the original post in this thread.

Grab the chmog script from here:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)
make it executable
$ chmod +x chmog
and copy it to your ~.gnome2/nautilus-scripts/
directory.  You now can right click -->scripts --> change permissions recursively

Under the surface, Gnome is much more confirurable than Kde.

Bob

---

### Post by Chris Ferrell on 2005-02-18
[QUOTE=Ironi]As an individual Ubuntu desktop user, I should care because...?[/quote]

You might not care.  I care because we are in the business of selling Linux applications and licenses affect us and others as well as knowing where the current trends are (Sun, RedHat, Novell, and now Ubuntu).
 
 
  
 
 > Again, IANAL. Are you claiming to be one? I've never heard of such "common knowledge," so perhaps you could provide links from authorative sources? It should be quite easy to prove if it's as common as you say, right?
 
Here's Bruce Perens, of UserLinux, and all around Unix/Linux industry insider on why QT as a standard isn't going to fly.  [http://www.userlinux.com/about/faq](http://www.userlinux.com/about/faq)
The bottom line is that QT can never be a standard toolkit for Linux with straight GPL as its license.  You can't expect businesses to pay $1500/developer/OS for a toolkit when all the other toolkits are free.  Even Microsoft's SDKs are free for the download. 

Once again, ask yourself the question what are the reasons that RedHat, Sun, Novell, and now Ubuntu (which coincidently Bruce Perens and UserLinux get compared to), chose Gnome.
 
 > I don't know -- perhaps because GNOME is a better fit for users that aren't so technically inclined as, say, myself? History has shown several times that technical superiority does not guarantee victory over lesser competition (see also: Beta vs. VHS, Alpha vs. x86, et. al.). GNOME also seems to please usability afficiandos (to put it mildly).

I'm a programmer and switched to Gnome about two years ago, as many other technical people have.  For me, it came down to a functional desktop that wasn't so cluttered with a developer-friendly license.

---

### Post by Ironi on 2005-02-18
[QUOTE=rkn]Under the surface, Gnome is much more confirurable than Kde.
 [/QUOTE]
 Erm, no. Since they're both open source, they're both equally configurable -- from the programmer's perspective. From the user's perspective, however, KDE is actually far more configurable. If you compare most GNOME apps to an equivalent KDE app (nautilus vs. konqueror, gnome-terminal vs. konsole, gedit vs. kate, totem vs. kaffeine, rhythmbox vs. amarok, ...), you'll discover that KDE apps actually expose more options to the user than GNOME apps do (even via gconf).
 
 BTW: [http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html)
 
 [QUOTE=Chris Ferrell]
 The bottom line is that QT can never be a standard toolkit for Linux with straight GPL as its license. You can't expect businesses to pay $1500/developer/OS for a toolkit when all the other toolkits are free. Even Microsoft's SDKs are free for the download.
 [/QUOTE]
 Perhaps TrollTech's pricing is too high, but that's beside the point. The dual licensing just enforces that companies must either contribute code back to the community (if their binary app is distributed) or pay to keep their changes private. I, personally, see no problem with that.
 
 BTW, the licensing has absolutely no bearing on *use*. KDE could well be the standard corporate desktop with no worries -- until someone wants to change and distribute the code, anyways.
 
 > 
 I'm a programmer and switched to Gnome about two years ago, as many other technical people have. For me, it came down to a functional desktop that wasn't so cluttered with a developer-friendly license.
 
 The GPL *is* a developer-friendly license; you just don't like some of its stipulations, apparently. I, OTOH, am fine with them. I've seen what keeping the code closed leads to (witness Microsoft as the worst-case scenario). I'm a firm believer in the Free (as in freedom) Open Source Software ideal, and the GPL embodies that ideal. It guarantees that someone can't take my Free GPL code, change it enough to break compatibility, and sell an "enhanced" version (otherwise known as "embrace and extend").
 
 If you so adamantly oppose the GPL's ideals, maybe you're in the wrong place, and are using the wrong OS. :)

---

### Post by Darrena on 2005-02-18
[QUOTE=AndersAA]about menu updating in gnome... it will be there, of course they are not gonna turn that off.  It's broke in the current test versions because of some changes to get that system to work better, dont worry, they'll get it working for final.[/QUOTE]

Anders, is this confirmed?  The reason I ask is that elsewhere I have been told that it will be removed and not put back in for 2.10.  I really hope that you are correct!  If so it will make the change to Hoary much easier!

This thread off the dev mailinglist is why I thought that a menu editor was not going to happen:
[http://www.ubuntuforums.org/showthread.php?p=70410#post70410](http://www.ubuntuforums.org/showthread.php?p=70410#post70410)

---

### Post by Chris Ferrell on 2005-02-18
Ironi,

Yeah, certain KDE advocates don't like to hear realities of QT license.  If glibc had the same license as QT then it would have to be re-written, since obviously not everything is going to be GPL.  Your personal philosophical beliefs are irrelevant to the situation.

---

### Post by JackDog on 2005-02-18
[QUOTE=Chris Ferrell]
 You might not care. I care because we are in the business of selling Linux applications and licenses affect us and others as well as knowing where the current trends are (Sun, RedHat, Novell, and now Ubuntu).
      [/QUOTE]
   You dont link against GPL code with this applications you are selling do you? 
   
   
   [QUOTE=Chris Ferrell]
     Here's Bruce Perens, of UserLinux, and all around Unix/Linux industry insider on why QT as a standard isn't going to fly.  [http://www.userlinux.com/about/faq]("http://www.userlinux.com/about/faq")
 The bottom line is that QT can never be a standard toolkit for Linux with straight GPL as its license. You can't expect businesses to pay $1500/developer/OS for a toolkit when all the other toolkits are free. Even Microsoft's SDKs are free for the download. 
     [/QUOTE]
     First Perens did not write the Qt comments...
   
 That FAQ appears to have been written in January04. Its over a year old, the licensing has changed several times. Now, anyone can download the SDK and make their own apps for linux or windows. No one "has" to pay $1500 to anyone. You only do if you plan on selling a commercial product that links to Qt. 
     
 On its merits Qt is a more advanced tookkit. It goes far and beyond what GTK will be able to do in 2-3 more years. Its natively object oriented and uses modern design patterns. I like and use both toolkits, I just dont like untruth's being spread. If I had to choose between the two, I would take Qt everytime. For an open source developer, the licenses are nearly identical in some ways. 
     
 The GPL is not about "freedom". If it was, anyone could do anything with software linking to GPL'd code. Sell it, call it their own and distribute it however they want to. The complaints the FAQ makes about Qt linking to the GPL'd code are valid, from a GPL point of view. How many apps link against GPL'd code that dont follow it.... Far too many to list. Even some linux kernel modules dont. 
   
 Last time I checked Open Source was the paramount idealogy. Not one man's (RMS) political agenda. Forcing a license upon someone completely goes against the idea of personal freedom. Dual licensing in my mind is by far the best license available. It allows companies/people to make money off their work and also give the open source community a kickback. Anyone can use code, and software in production environments as long as they give credit where it is due.
    
 Qt is growing very fast now with license change for the windows toolkit. I would not be suprised if Qt becaome the de facto standard for open source apps in 2-3 years. This was a very smart move by trolltech. Corporations like dealing with corporations. I think GTK will still be used as it should, but it will see its "market share" decrease or hold pat.
   
   **Novell is definitely not dropping KDE**. No one is (tm). KDE is as powerful as ever and is pulling away fast in certain markets. Gnome is also growing (albeit a little slower) but with a different focus. They want the average user. KDE wants the power user and possibly the average user in the future. KDE4 could delt quite a blow to gnome's market share and possibly the developer base. 
   
  
  
   In other news.... Did you know that KDE is....
 -porting over the exchange connector to kontact? Checkout the kontact page and see how many groupware servers kontact now supports....  They need more developers to help though. 
 -developing a kpart for gecko? Konq users can switch between khtml and gecko on the fly. Combine that with all the other kparts and konqueror is fast becoming the most advanced all purpose browser ever.
-now supports hal (3.4b2). Type media:/ in the location bar... or one of the other new slaves. 
  -finally ditched Keramik in favour of Plastik. Yay!
  
 I hope that Gnome uses KDE as motivation to start listening to the community. KDE has excellent communication with its community and it is showing. KDE users are getting what they want, and sometimes things they didnt know they needed but now cant live without (konq in my case). Spatial Nautilus is a prime example of Gnome pissing people off. Some enough to drop gnome completely. 
  
  It is nice to have so many choices for graphical interfaces =)

---

### Post by Chris Ferrell on 2005-02-18
JackDog

This is what you said, which is blatantly false.

*Slackware, HP, RedHat and supposedly Novell/Suse (yeah, I know, evolution, separate discussion) are dropping gnome because of the lack of cooperation and progress in developing a desktop environment for the corporate world.*

---

### Post by Ironi on 2005-02-18
[QUOTE=Chris Ferrell]Ironi,
    
 Yeah, certain KDE advocates don't like to hear realities of QT license. If glibc had the same license as QT then it would have to be re-written, since obviously not everything is going to be GPL. Your personal philosophical beliefs are irrelevant to the situation.[/QUOTE]
 Okay, fair enough. TrollTech might switch to the LGPL for QT-Free eventually (especially if not doing so starts to impact their business too negatively), but who can say? As far as I can tell, it doesn't much matter right now -- there aren't too many high-quality closed source applications for Linux anyways.
    
    I'd prefer that companies use GTK for CSS Linux apps, anyways. QT sans kdelibs is fugly, as Opera clearly demonstrates. :o
    
    [QUOTE=JackDog]
 The GPL is not about "freedom". If it was, anyone could do anything with software linking to GPL'd code. Sell it, call it their own and distribute it however they want to.
    [/QUOTE]
 Yes, it is about freedom. [The GPL](http://www.gnu.org/copyleft/gpl.html) stipulates that licensed code must always be made available to those who receive the compiled application. Further, it gives anyone who receives the code the right to modify, compile, and redistribute it, as long as they abide by the first rule as well. It's not as liberal as [the BSD license](http://www.opensource.org/licenses/bsd-license.php) (which will allow companies to incorporate covered code into CSS without returning anything), but it does promote enforced freedom with its rules.

---


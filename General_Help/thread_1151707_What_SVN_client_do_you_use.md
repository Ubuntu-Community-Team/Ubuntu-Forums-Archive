---
title: "What SVN client do you use?"
date: 2009-05-07
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-05-07
Hi, I have an SVN issue and actually it's the main blocker that doesn't let me fully switch to Linux.

I played with this around a month ago and if I remember correctly, I installed RapidSVN from repostitory (and a few other programmes but they were totally horrible). I spent huge amount of time on RapidSVN and googled very hard but I didn't manage to make this stupid RapidSVN remember my password. So every time I entered our repo it asked me to enter password for each folder and file that was in that folder. :-x:-x:-x
Could you tell me what do you use for working with SVN? I can't believe that there is no normal program for SVN because as far as I know Linux community mainly consists of computer geeks. :) On windows I work with TortoiseSVN and find it very very nice. It lets me easily browse repo, marks changed folders with icons, lets browse revisions and has a very nice TortoiceMerge that allows me to see changes in a specific file. Could you tell me is there any Linux SVN client close by functionality to the one I described? :)

---

### Post by Eugene_Bondarenko on 2009-05-07
*up*

---

### Post by Eugene_Bondarenko on 2009-05-07
[COLOR="Blue"]**To Moderators:**[/COLOR]
Uhhh....sorry, I guess I posted this topic in a wrong place. Could you move it to 
Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming > Programming Talk 
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Kareeser on 2009-05-07
The package "subversion" is exactly the same as TortoiseSVN, since Tortoise is simply a GUI frontend to the program itself.

Type "svn help" to get some help regarding the program itself :)

I don't know of any Linux GUI frontends to SVN... but only 'cause I've never looked, not becuase there aren't any.

---

### Post by kirsis on 2009-05-07
I was once upon a time in the same situation you are now - trying to find a decent TortoiseSVN like GUI for svn on Linux.

There ain't one (there are some halfassed attempts but nothing worth using, imo).

I'm afraid you'll have to get used to using it from the command line

---

### Post by Eugene_Bondarenko on 2009-05-07
> **Kareeser said:**
> The package "subversion" is exactly the same as TortoiseSVN, since Tortoise is simply a GUI frontend to the program itself.

Type "svn help" to get some help regarding the program itself :)

I don't know of any Linux GUI frontends to SVN... but only 'cause I've never looked, not becuase there aren't any.

No no, I mean a GUI client for the SVN client. I don't need to maintain the repositary. I am a developer and all I need to do is to have a quick and easy access to our files and to all the things (log messages, changes,...) that happen there. 



> **kirsis said:**
> I was once upon a time in the same situation you are now - trying to find a decent TortoiseSVN like GUI for svn on Linux.

There ain't one (there are some halfassed attempts but nothing worth using, imo).

I'm afraid you'll have to get used to using it from the command line

OMG, that sounds very weird. :(  I thought a cool SVN client GUI was one of the first developed because all open-source developers very often work with it. I am really not sure if I'll switch from my nice Windows TortoiseSVN to command line.

---

### Post by kirsis on 2009-05-07
> **Eugene_Bondarenko said:**
> OMG, that sounds very weird. :(  I thought a cool SVN client GUI was one of the first developed because all open-source developers very often work with it. I am really not sure if I'll switch from my nice Windows TortoiseSVN to command line.


Well, thing is, OSS developers likely enjoy using the CLI so it isn't a high priority to GUI-ify the process.

Btw, I do have one suggestion. If you use the Eclipse IDE, then there's an extension called Subclipse.  

That worked pretty well for me, actually. Though I didn't use it very extensively (I'm not a fan of IDEs)

---

### Post by Eugene_Bondarenko on 2009-05-07
Thanks, I'll check that out however I have to say that I hate IDEs too. All I want from the development environment is nice color highliting and a tree of classes that lets me easily navigate in huge files.

---

### Post by Alterax on 2009-05-07
I may be able to help out here.  Most of your IDE environments--netbeans, anjuta, and I'm fairly sure Eclipse all have extensions which let you work with SVN from within the IDE itself.

Personally, I use svn for more than programming (it's great for a writer, believe it or not!) so for that I use SVN Workbench, which I'm rather fond of.

---

### Post by Kareeser on 2009-05-07
Wait, so... all you're doing is checking out and updating?

You can do the same with the commands "svn co" and "svn commit"

---

### Post by Eugene_Bondarenko on 2009-05-07
> **Alterax said:**
> I may be able to help out here.  Most of your IDE environments--netbeans, anjuta, and I'm fairly sure Eclipse all have extensions which let you work with SVN from within the IDE itself.

Personally, I use svn for more than programming (it's great for a writer, believe it or not!) so for that I use SVN Workbench, which I'm rather fond of.
LOL, you really found a non-standard use of SVN. :D  Thanks for the advice, I'll google for that workbench and try it out soon.



> **Kareeser said:**
> Wait, so... all you're doing is checking out and updating?

You can do the same with the commands "svn co" and "svn commit"
Well, updates and checkouts are the main things I deal with but it's not the only. I like very much when TortoiseSVN changes icons for the changed files. So I enter the directory with my project and immediately see what has been changed. Also there are few other features I can't live without. They are "Show Changes" and "Show Log". In show log I can see previous commits. For example I find some weird line of code that was not here before. I go to "Show Log" and see all the commits. Then enter "dir/some_file.php" in the search window and see that a week ago developer X commited this file. Then I click on it and select "Show Changes". And tortoiseSVN shows me in a very comfortable way what lines have been changed. And here I get a chance of understanding why that weird line is there. :)

---

### Post by sa-mejia on 2009-05-07
There are at least two GUI front ends for SVN in Ubuntu (and another one at least that I've heard for Kubuntu).

[http://code.google.com/p/nautilussvn/](http://code.google.com/p/nautilussvn/) attempts to be just a clone of Tortoise, so this is your best bet.  I use it with Hardy, and have had my problems (the later one: [http://ubuntuforums.org/showthread.php?p=7232509#post7232509](http://ubuntuforums.org/showthread.php?p=7232509#post7232509)).  But I believe that with Intrepid is works a lot better.

The other one is a group of Nautilus scripts  ([http://marius.scurtescu.com/2005/08/24/nautilus_scripts_for_subversion](http://marius.scurtescu.com/2005/08/24/nautilus_scripts_for_subversion)).  You can install it from your repository.  The package is called nautilus-script-collection-svn.  I have not used it.

Santiago.

---

### Post by Eugene_Bondarenko on 2009-05-07
Wow, thanks much!!! Judging from the screenshots nautilussvn is exactly what I need!

---

### Post by Alterax on 2009-05-07
> **sa-mejia said:**
> There are at least two GUI front ends for SVN in Ubuntu (and another one at least that I've heard for Kubuntu).

[http://code.google.com/p/nautilussvn/](http://code.google.com/p/nautilussvn/) attempts to be just a clone of Tortoise, so this is your best bet.  I use it with Hardy, and have had my problems (the later one: [http://ubuntuforums.org/showthread.php?p=7232509#post7232509](http://ubuntuforums.org/showthread.php?p=7232509#post7232509)).  But I believe that with Intrepid is works a lot better.

The other one is a group of Nautilus scripts  ([http://marius.scurtescu.com/2005/08/24/nautilus_scripts_for_subversion](http://marius.scurtescu.com/2005/08/24/nautilus_scripts_for_subversion)).  You can install it from your repository.  The package is called nautilus-script-collection-svn.  I have not used it.

Santiago.

ROCK ON!  I've wanted a client that integrates into Nautilus for quite a while now; one of these may be just what I'm looking for!:guitar:

---

### Post by Kareeser on 2009-05-07
Good to know there's an Ubuntu variant. Looks to be similar to Tortoise, if not a clone.

---

### Post by sa-mejia on 2009-05-07
nautilussvn is really neat.  And the developers are also very helpful.  Whenever I have had problems in the past, they have been very quick to answer.

Santiago.

---

### Post by Eugene_Bondarenko on 2009-05-08
Yeah, absolutely true. I had some problems when checking out and they helped me with everything in IRC. And, yeah, it's almost 100% clone of tortoise. It even recognized my tortoise checkouts on windows partition. :)

---

### Post by Eugene_Bondarenko on 2009-05-08
The last thing I have to finish is to make this openSSH window remember my password :)

---

### Post by infestor on 2010-04-19
i use **kdesvn**
but still couldn't find a way to save my svn+ssh password. i have to enter my password at least 2 times to *kwallet* whenever i do an operation (update, diff, etc..).

---

### Post by Eugene_Bondarenko on 2010-04-19
I am using NautilusSvn right now and I managed to get "remember password" functionality by using Public/Private Keys. Strictly speaking the keys are not related to the SVN client of your choise, they are related to SSH itself. Here is an article that will walk you through the process
[http://swik.net/Ubuntu/Only+Ubuntu/How+to+Create+Passwordless+SSH+Private%2FPublic+Key+Pair+on+Ubuntu/b5t6e](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Create+Passwordless+SSH+Private%2FPublic+Key+Pair+on+Ubuntu/b5t6e)

---

### Post by Chronon on 2010-04-19
I never really saw the reason for using a GUI for SVN.  Of course, I only do simple things like checking out trunk, patching and building, which are all most easily done from CLI.

---

### Post by webtechquery on 2010-07-06
Hi.

Finding out the best alternatives to Tortoise SVN for Ubuntu or Linux, I found RapidSVN as a good one before. But after that, I think one of the best alternative to Tortoise SVN is Rapid VCS (previous known as Nautilus SVN).

You can have a try on both of them, by going through the following link:
[http://www.webtechquery.com/index.php/2010/05/free-svn-tools-ubuntu-free-svn-software-ubuntu/](http://www.webtechquery.com/index.php/2010/05/free-svn-tools-ubuntu-free-svn-software-ubuntu/)

Thanks

---


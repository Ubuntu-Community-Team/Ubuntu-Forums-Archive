---
title: "Why no openoffice 2 package?"
date: 2005-10-28
forum: Desktop Environments
---

### Post by DavidTangye on 2005-10-28
I installed oo 2, via Synaptic, but its actually the 1.9 pre-release. Why does there not exist an up to date package for this very high profile application?:confused:

---

### Post by matthew on 2005-10-28
Because the changes that occurred between 1.9.129 and 2.0 were trivial and compiling OpenOffice takes a long time and is a lot of work.

---

### Post by egraham23 on 2005-10-29
OpenOffice2 was just made available a few days ago, and I know that it takes a little time for software releases to make it onto the repos. I don't know of an official ETA, but I imagine the package will be available soon. There is work that goes into making and posting the packages for Ubuntu, and I'm sure it's just a matter of time.

---

### Post by abou on 2005-10-29
Actually, it won't.  The Ubuntu repos are frozen for 6 months and unless there is a major release nothing changes.  As Matthew mentioned, the changes between v1.9.x and 2.0 seem trivial and therefore OOo 2 final will not be in the Breezy repos.  They will, however, be there for Dapper Drake.

---

### Post by aysiu on 2005-10-29
[QUOTE=abou]Actually, it won't.  The Ubuntu repos are frozen for 6 months and unless there is a major release nothing changes.  As Matthew mentioned, the changes between v1.9.x and 2.0 seem trivial and therefore OOo 2 final will not be in the Breezy repos.  They will, however, be there for Dapper Drake.[/QUOTE] Do you have an official source for this? I read something similar on another thread, too, implying that software never gets updated until a new Ubuntu release (i.e., every six months), and I just haven't found that to be true. For example, I distinctly remember in Hoary doing a ```
sudo apt-get upgrade
``` and bumping up my Firefox 1.0.4 (or whatever came with Hoary) to 1.0.7. And over the last six months, I've done numerous of these upgrades, finding a bunch of my applications updated to newer versions (not just the libs and such).

Again, is there an official source for this? I tried looking on the wiki and the official Ubuntu site, but I couldn't find a definitive answer. If it's not true, I'd appreciate people not spreading this lie around. If it is true, I'd like to *know* it's true, not just hear hearsay.

---

### Post by DavidTangye on 2005-10-29
When 1.9 installs it does not include a start icon for the 'Base' component, ie the MS Access desktop database "equivalent". So I assumed it was not there in 1.9, as it supposedly is in the 2.0 release. If that is so, that is not trivial... Or do I need to look in the Calc and Writer components to get at the Base functionality?

---

### Post by Hairy_Palms on 2005-10-29
base is there, they just hide the menu icon by default for some reason, and if you want the real 2.0 go to the thread at [http://www.ubuntuforums.org/showthread.php?t=83308](http://www.ubuntuforums.org/showthread.php?t=83308)

---

### Post by MichaëlVD on 2005-10-29
[QUOTE=aysiu]bumping up my Firefox 1.0.4 (or whatever came with Hoary) to 1.0.7. And over the last six months, I've done numerous of these upgrades, finding a bunch of my applications updated to newer versions[/QUOTE]

Security updates such as Firefox 1.0.7 are a different thing.

---

### Post by aysiu on 2005-10-29
[QUOTE=MichaëlVD]Security updates such as Firefox 1.0.7 are a different thing.[/QUOTE] So the Ubuntu developers look at all the packages for updates. If they determine the version update to be because of security reasons (based on the release notes, I guess), then they update that in the repositories? If not, they just save that update for the next Ubuntu release? Is that what you're saying?

And none of this is true if you use the backports, correct?

---

### Post by DavidTangye on 2005-10-29
Great, it appears that a debian package for OOo 2 exists.

I went to "http://www.ubuntuforums.org/showthread.php?t=83308" and tried to add the line "deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./" into /etc/apt/sources.list as instructed there, but that results in an error "Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)"

I tried "deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) hoary universe" as well but still an error. It would help if I understood apt better.

What is the correct line for sources.list?

---

### Post by abou on 2005-10-29
To be honest Aysiu, I've read it in a bunch of places.  So, as [Micha&#235;lVD said, with Firefox there was a security update which necessitated updating the repositories.]("member.php?u=21600")

Oddly enough, I heard that there was a show-stopping bug in OOo 2 RC2 and so I imagine that would still be in v 1.9.x.

---

### Post by Hairy_Palms on 2005-10-29
i updated as it says at [http://www.ubuntuforums.org/showthread.php?t=83308](http://www.ubuntuforums.org/showthread.php?t=83308) because in the prerelease if i went to options it closed.

---

### Post by aysiu on 2005-10-29
[QUOTE=abou]To be honest Aysiu, I've read it in a bunch of places.  So, as [MichaëlVD said, with Firefox there was a security update which necessitated updating the repositories.]("member.php?u=21600")[/quote] For some reason that link isn't working. Can you update it? Can you also tell me what these bunch of places are? I've also read "a bunch of places" that Ubuntu is a lousy OS, but I'd like to hear this from some kind of official source, if possible. I'm not saying it's definitely not true, but I'd like to know definitively so I can answer people correctly when they ask.

---

### Post by tageiru on 2005-10-29
[QUOTE=MichaëlVD]Security updates such as Firefox 1.0.7 are a different thing.[/QUOTE]
Actually it was not security that was the reason for bumping the firefox version. Security was handled by backporting patches from firefox head to the version in the ubuntu repository.

Firefox was bumped because extensions and themes did not work any more.

---

### Post by abou on 2005-10-29
[quote=aysiu]For some reason that link isn't working. Can you update it? Can you also tell me what these bunch of places are? I've also read "a bunch of places" that Ubuntu is a lousy OS, but I'd like to hear this from some kind of official source, if possible. I'm not saying it's definitely not true, but I'd like to know definitively so I can answer people correctly when they ask.[/quote]Oh, that wasn't a link to anything actually.  I copied Michael's name from his post and I guess it copied a link to his profile, which then continued until the end of the sentence.

I can look around and see what comes up.

---

### Post by aysiu on 2005-10-29
Thanks. I just want to know what the official line is. Being forum staff doesn't make me any more privy to what the policies of Ubuntu are. I tried looking on the official Ubuntu Linux site, but I couldn't find anything on this.

---

### Post by angrykeyboarder on 2005-10-29
[quote=abou]Actually, it won't. The Ubuntu repos are frozen for 6 months and unless there is a major release nothing changes. As Matthew mentioned, the changes between v1.9.x and 2.0 seem trivial and therefore OOo 2 final will not be in the Breezy repos. They will, however, be there for Dapper Drake.[/quote]

There are actually bugs (I don't know this for a fact it's just what I've read) in the version we're stuck with for now, so unless and untill they get the attention of the developers or if another bug pops up in 2.0 we'll be stuck till dapper.

Of course, there's nothing stopping one from grabbing it from the dapper repo when it becomes available.

---

### Post by angrykeyboarder on 2005-10-29
[quote=matthew]Because the changes that occurred between 1.9.129 and 2.0 were trivial and compiling OpenOffice takes a long time and is a lot of work.[/quote]

There were quite a few version changes in the beta cycle and we got those. What made them so much easier to comple than the final version?

That excsuse I don't buy.  What I do believe is that we were just unfortunate and missed the boat.  Had Breezy been released a few weeks later, we'd have 2.0 now.

---

### Post by NewbieNik on 2005-10-29
The question here is, OK so its 1.9.29...is that really a problem? or are we so Window led that we have to have the new version even if the old one works fine?
I'm not criticizing anyone..don't get me wrong, but a lot of users tend to think that the newest version will cure all their problems and blame the OS when it turns out to be bugged!

---

### Post by leech on 2005-10-29
[QUOTE=NewbieNik]The question here is, OK so its 1.9.29...is that really a problem? or are we so Window led that we have to have the new version even if the old one works fine?
I'm not criticizing anyone..don't get me wrong, but a lot of users tend to think that the newest version will cure all their problems and blame the OS when it turns out to be bugged![/QUOTE]

I would agree with you, except that version 1.9.x is considered the pre-release version, not the final version.  So basically there ARE bugs that prevented it from being released, and so the Ubuntu guys should be putting this in the final repositories.  

I think the main reasons why they don't want to, is because a) it's not a security related thing, and b) OpenOffice isn't exactly small.  So for people who have dial-up, they don't want to be like MS and have a huge update for the OS just after installing it.

Personally, I think they should put the 2.0 in the repositories, and then re-create the ISOs to include it as well.  

Leech

---

### Post by mcframe on 2005-10-30
[QUOTE=leech]So basically there ARE bugs that prevented it from being released, and so the Ubuntu guys should be putting this in the final repositories.  
[/QUOTE]
I completely agree with you, we use (K)ubuntu 5.10 in the productive environment of our small company and there are several 1.1.3 documents that are simply unsusable under 1.9.129 because of some (to us) severe bugs. We have posted them already to the related bug tracking systems and it is quite interesting to see that those bugs seems to be Ubuntu specific, because they dont show up on OO-Beta2 releases on diffierent distros (although they are 100% reproducable on any virgin installation of breezy). 

I would really ask the maintainers of Breezy to provide a greatly bug-fixed version of OO which to our opinion should then be the final OO2 and even put this updates to the ISOs as well.

---

### Post by DavidTangye on 2005-10-30
I have now added the line -

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

into Synaptic as a "Custom" repository. Synaptic now gives the same 1.9.79 version of OOo2 as before from archive.ubuntu...., plus the 2.0 version from people.ubuntu... It now also shows  Base 2.0, which had NO equivalent in 1.9.79. In other words, the prelease version does NOT have Base in it. :( 


When I try to install any OOo 2.0 package I get dependency errors. It seems that [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) depends on another repository. Its all beyond me, and I have no more time right now to keep mucking around with it. So for now I have dropped the doko repository, and am re-downloading 1.9.79 :( to reinstall it.

Can anyone who has successfully used [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) please show us their /etc/apt/sources.list file.

---

### Post by manicka on 2005-10-30
[QUOTE=DavidTangye]I have now added the line -

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

into Synaptic as a "Custom" repository. Synaptic now gives the same 1.9.79 version of OOo2 as before from archive.ubuntu...., plus the 2.0 version from people.ubuntu... It now also shows  Base 2.0, which had NO equivalent in 1.9.79. In other words, the prelease version does NOT have Base in it. :( 


When I try to install any OOo 2.0 package I get dependency errors. It seems that [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) depends on another repository. Its all beyond me, and I have no more time right now to keep mucking around with it. So for now I have dropped the doko repository, and am re-downloading 1.9.79 :( to reinstall it.

Can anyone who has successfully used [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) please show us their /etc/apt/sources.list file.[/QUOTE]


sounds like you need to add the universe and multiverse repos as well

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by kevin1 on 2005-10-30
I agree that the bugs in 1.9.129 are far more than trivial. I tried several complete removal / reinstalls, but was plagued by frequent key-freezes and crashes. In desparation I also installed 1.1.15, but while stable, this did not support open document format.

I have now downloaded and installed 2.0.0 from [http://www.openoffice.org/]("http://www.openoffice.org/") and have had no problems over several hours of use.

For anyone else who wants to try this route, here are the details of the procedure I used:

1.  Use Synaptic to do a 'complete removal' of both versions.
2.  I did 'sudo locate -u' followed by 'locate openoffice' which revealed a mass of stuff left behind, all over the system. I deleted some of these files by hand, but there was so much that I gave up.
3.  Download the 2.0.0 RPM archive to a convenient folder, e.g. ~/temp.
4.  Unarchive the file - I used right-click then 'extract here' in Nautilus.
5.  Delete all menus from ~/Temp/RPMS/desktop-integration, except for 'openoffice.org-debian-menus_2.0.0-3_all.deb'.
6.  'Alien' is required convert the RPM files to Debian files. It is not installed by default in Breezy, so search for 'alien' in Synaptic and install it.
7.  In a terminal cd to ~/Temp/RPMS, then do 'sudo alien -d *.rpm', followed by 'rm *.rpm'.
8.   To install OpenOffice do 'sudo dpkg -i *.deb', followed by 'sudo chmod 555 /opt/openoffice.org2.0/program/soffice'
9.  To install the OpenOffice entries in the Gnome menu,  cd to ~/Temp/RPMS/desktop-integration then do 'sudo dpkg -i openoffice.org-debian-menus_2.0.0-3_all.deb.
10. Restart the Gnome panel by 'killall gnome-panel'.

Good luck,

Kevin

---

### Post by angrykeyboarder on 2005-10-30
[quote=leech]I would agree with you, except that version 1.9.x is considered the pre-release version, not the final version. So basically there ARE bugs that prevented it from being released, and so the Ubuntu guys should be putting this in the final repositories. 

I think the main reasons why they don't want to, is because a) it's not a security related thing, and b) OpenOffice isn't exactly small. So for people who have dial-up, they don't want to be like MS and have a huge update for the OS just after installing it.

Personally, I think they should put the 2.0 in the repositories, and then re-create the ISOs to include it as well.  

Leech[/quote]

In the final weeks before OOo 2 final was released OOo released several  betas.  If you were using Breezy then (prior to it's final release) as I was, you saw several updates to OOo.  I recall updating at least 3 times in the month or so prior to the release of Breezy.

So apparantly it's not too big a deal.

But I just think they are treating it like any other packages.  Unless there is a security-related issue or a major bugfix, you won't see any updates to OpenOffice.org in Ubuntu until Dapper is released.

---

### Post by angrykeyboarder on 2005-10-30
[quote=kevin1]I agree that the bugs in 1.9.129 are far more than trivial. I tried several complete removal / reinstalls, but was plagued by frequent key-freezes and crashes. In desparation I also installed 1.1.15, but while stable, this did not support open document format.

I have now downloaded and installed 2.0.0 from [http://www.openoffice.org/]("http://www.openoffice.org/") and have had no problems over several hours of use.

For anyone else who wants to try this route, here are the details of the procedure I used:

1.  Use Synaptic to do a 'complete removal' of both versions.
2. I did 'sudo locate -u' followed by 'locate openoffice' which revealed a mass of stuff left behind, all over the system. I deleted some of these files by hand, but there was so much that I gave up.
3.  Download the 2.0.0 RPM archive to a convenient folder, e.g. ~/temp.
4.  Unarchive the file - I used right-click then 'extract here' in Nautilus.
5.  Delete all menus from ~/Temp/RPMS/desktop-integration, except for 'openoffice.org-debian-menus_2.0.0-3_all.deb'.
6. 'Alien' is required convert the RPM files to Debian files. It is not installed by default in Breezy, so search for 'alien' in Synaptic and install it.
7.  In a terminal cd to ~/Temp/RPMS, then do 'sudo alien -d *.rpm', followed by 'rm *.rpm'.
 8.   To install OpenOffice do 'sudo dpkg -i *.deb', followed by 'sudo chmod 555 /opt/[openoffice.org2.0/program/soffice]("http://openoffice.org2.0/program/soffice")'
9. To install the OpenOffice entries in the Gnome menu, cd to ~/Temp/RPMS/desktop-integration then do 'sudo dpkg -i openoffice.org-debian-menus_2.0.0-3_all.deb.
10. Restart the Gnome panel by 'killall gnome-panel'.

Good luck,

Kevin[/quote]

So you're saying adding "
 
 deb [http://people.ubuntu.com/~doko/OOo2]("http://people.ubuntu.com/%7Edoko/OOo2") ./" to your sources.list file didn't work for you?

It worked great for me.  It just upgraded all my exisiting 1.9... packages.  So far, so good.

---

### Post by unexpected on 2005-10-30
Unrelated to your question a bit, but if you read the change log, you'll realize that there's hardly any changes from the version Ubuntu has and the official 2.0 that came out a few days ago.

1.9 is not a different version, it is merely the 2.0 beta. OO.o2 had been in beta for 6 months, so this beta version is highly stable. If you read other people's posts after installing OO.o2 you'll see that they don't really notice any difference.

I'm sure it will be included in the Backports, once development on them start.

I wish you will in trying to install the new version, I'm just not sure if it's going to be worth your effort.

---

### Post by DavidTangye on 2005-10-30
[QUOTE=angrykeyboarder]So you're saying adding "
 
 deb [http://people.ubuntu.com/~doko/OOo2]("http://people.ubuntu.com/%7Edoko/OOo2") ./" to your sources.list file didn't work for you?

It worked great for me.  It just upgraded all my exisiting 1.9... packages.  So far, so good.[/QUOTE]

Can you please post your sources.list file to here? I think there might be another repository that is needed ... hmm unless ... maybe you have other software installed - Do you have KDE installed?

---

### Post by angrykeyboarder on 2005-10-31
[quote=unexpected]I wish you will in trying to install the new version, I'm just not sure if it's going to be worth your effort.[/quote]

I added another line to my sources.list file and installed the upgrades.  It went just as easy as upgrading any other packages.

---

### Post by angrykeyboarder on 2005-10-31
[quote=DavidTangye]Can you please post your sources.list file to here? I think there might be another repository that is needed ... hmm unless ... maybe you have other software installed - Do you have KDE installed?[/quote] 
My sources.list file isn't the example you're looking for. It's rather um.. "messy" but many others have completed the upgrade with no problem so you might ask around.

Someone did ask if you had the universe repository enabled. I'm not sure why that would make a difference though.

Did you follow the (unusual) syntax on that URI?

Oh and yes, I do have KDE installed. I initially did an "apt-get install kubuntu-desktop" after installing Ubuntu from CD.

---

### Post by DavidTangye on 2005-10-31
Hooo boy ... I think I just guessed what my problem is with using the doko repository. I am still on 5.04 "Hoary Hedgehog", and I am guessing that the doko repository assumes you are running Breezy.

---


---
title: "OpenOffice question"
date: 2006-02-14
forum: Desktop Environments
---

### Post by seakiwi on 2006-02-14
I'm currently using the version of OpenOffice that came with the install CD for Kubuntu. I understand there is a new version out which is not yet available from the repositories via Synaptic.

I decided to download the latest version with the intention of uninstalling the version I have first, then installing the new one. I just wasn't sure what would happen if I installed a .deb package via Terminal on top of the version that was already there.

However, when I went to uninstall it with Synaptic it was going to uninstall the Kubuntu-desktop too, so needless to say I cancelled that. I'm guessing that means that OpenOffice comes as part of the Kubuntu-desktop package and can't be removed separately.

So ... if I want the latest version do I just install it and hope it will overwrite the current version? Or should I wait for the updated version to show up in the repositories?

If anyone here is using the latest version, are there many significant differences?

TIA!

---

### Post by anirban.sam on 2006-02-14
the latest oO2.0.1 came with mostly internal bugfixes & visual enhancements, not much difference than the prev ver

---

### Post by Sutekh on 2006-02-14
[QUOTE=seakiwi]
However, when I went to uninstall it with Synaptic it was going to uninstall the Kubuntu-desktop too, so needless to say I cancelled that. I'm guessing that means that OpenOffice comes as part of the Kubuntu-desktop package and can't be removed separately.
[/QUOTE]

As said, not too many differences, but that shouldn't stop you. 

**kubuntu-desktop** is a *meta-package* meaning that it installs a lot of other programs for you, so you dont have to install dozens indivdually.  Removing kubuntu-desktop isn't a problem.

---

### Post by towsonu2003 on 2006-02-14
as others said, kubuntu-desktop is basically nothing but a list of other packages to be installed if the user decides to apt-get kubuntu-desktop. 

as for installing ooo, I would search the forums for a howto. that would be easier to do I guess.

---

### Post by seakiwi on 2006-02-15
[QUOTE=Sutekh]As said, not too many differences, but that shouldn't stop you. 

**kubuntu-desktop** is a *meta-package* meaning that it installs a lot of other programs for you, so you dont have to install dozens indivdually.  Removing kubuntu-desktop isn't a problem.[/QUOTE]

So if I uninstall Kubuntu-desktop I'm only uninstalling a list of programs? It won't uninstall any programs I've already got installed?

If that's the case why would the OpenOffice install require you to uninstall it? I don't understand why you should have to uninstall a list of packages in order to install a particular software.

Sorry if I sound dense but I don't get that :???: 

So would you recommend I uninstall the old version first, or just intall the new one over the top?

---

### Post by hollowhead on 2006-02-15
I don't use kubuntu (use Gnome/metacity or fluxbox) so I cannot comment on that but I would recommend you uninstall the old version first.  If you don't you have two versions the new in /opt/OOsomething and the old one in usr/share/?.  I installed the new one then found I had two and uninstalled them both using synaptic.  Weirdly unsintalling it led to synaptic insisting it had to download some large libs and the OO us dict.  I have dialup on my desktop and cancelled this part way through with no ill effects.  I then reinstalled from the rpm I'd downloaded at work from OO.org using alien and from the command line using dpkg.  Installation went fine, gnome users also install the gnome menu deb which adds the office suite to your menus.  

It is worth the upgrade.  There was no help included in the distro version.  Downloading this by synaptic for 1.9.x  which took ages and gave a broken helpfile with links and images missing.  Also the spellcheck didn't work the subject of many posts on this forum.  Both were fixed in version 2.0.x.. Then tried to install uk thesaurus which crashes the program... As a word processor I'd recommend abiword.

---

### Post by gingermark on 2006-02-15
[QUOTE=seakiwi]So if I uninstall Kubuntu-desktop I'm only uninstalling a list of programs? It won't uninstall any programs I've already got installed?

If that's the case why would the OpenOffice install require you to uninstall it? I don't understand why you should have to uninstall a list of packages in order to install a particular software[/QUOTE]

Yep.

kubuntu-desktop is a metapackage that includes the version of OpenOffice that came on the CD. So if you remove any of the programs on the list, then you don't have the full kubuntu-desktop package installed. So the metapackage is removed. This does have an advantage - you can always get back to the "kubuntu-desktop" state (poorly put), which will be useful when upgrading to Dapper for example.

---

### Post by treris on 2006-02-15
why not just use synaptic to install the latest version of OOo??

just add 'deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./ '
to your etc/apt/sources.list and reload all repositories using synaptic.

your openoffice will then 'automatically' be updated to the latest version (2.0.1??)

that's all

---

### Post by seakiwi on 2006-02-19
[QUOTE=treris]why not just use synaptic to install the latest version of OOo??

just add 'deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./ '
to your etc/apt/sources.list and reload all repositories using synaptic.

your openoffice will then 'automatically' be updated to the latest version (2.0.1??)

that's all[/QUOTE]

OK, I did this, but when I mark openoffice for upgrade I get a stack of "NOT AUTHENTICATED!" warnings. Is that something I should be concerned about? I don't recall getting that warning for any other upgrades I've done in the past.

---


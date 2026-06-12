---
title: "How can I delete these failed updates from my sources list??"
date: 2009-06-04
forum: General Help
---

### Post by -=Ghost=- on 2009-06-04
Hi Guys...

I am having a little trouble correctly configuring my repository sources lists. To download packages and uodates form various extra sources!

I am relatively new so please bare with me...

I have added a couple of extra repositories, ie':- :

Medibuntu and a couple of jaunty's free non-free repositories mainly for Multimedia purposes.

But when I run 'sudo apt-get update' I get these error messages at the end of the termonal! ::-

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

I Cannot find the above errors anywhere in my Sources list!

Here is the output from the :- 
'gksudo gedit /etc/apt/sources.list 
      Terminal output, to view my installed sources'.

 I cannot find the above update error anywhere in my sources list bellow! :-

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-security main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-security restricted main universe multiverse #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main universe multiverse #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty restricted deb-src
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty restricted
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free 

I have had a good look on this forum for a solution and also google'd for a fix. 
But I have had no joy.

How can I fix this?

does anyone know how I can rectify this, and also can you point out where I am going wrong?

Cheers in advance...

---

### Post by VMC on 2009-06-04
Anything is sources.list.d directory?

---

### Post by plucky on 2009-06-04
```
[code]# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-security main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-security restricted main universe multiverse #Added by software-properties
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main universe multiverse #Added by software-properties
[color=red]deb http://gb.archive.ubuntu.com/ubuntu/ jaunty restricted deb-src[/color]
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty restricted
deb http://packages.medibuntu.org/ jaunty free non-free 
```

The line in red is wrong.Put a # in front of it.
I recommend you remove the "proposed" repositories as some of the proposed updates can break you system and think about removing the backports repository until you are more experienced.

See this [backports link](https://help.ubuntu.com/community/UbuntuBackports)

The sources.list file is just the list of repositories that are used to install and update your software.You can use Software Sources under System > Administration to manage your sources.list if you are not comfortable with manually editing the file.

Good Luck

---

### Post by -=Ghost=- on 2009-06-05
Thank-you all for your replies...

I cannot update at all at the moment!

I have not tried any of your suggestions yet.
But when I booted up today I noticed A red circle eith a white line in the middle that gave me the error message:-

Could NOT initialise the package information

An unresolved problem occured while initialising the package information.

Please report the bug for the 'update-manger' package and try and include the following message:

'E:Malformed line 35 in source list /etc/apt/sources.list (distparse),
E:the list of sources could not be read,'

Can anyone help me fix this??

---

### Post by -=Ghost=- on 2009-06-05
Hi plucky..

I tried your suggestions. and it seemed to fix my issue (sort of) At least I can update know!

But I still get this error message:-

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/source/Sources in Meta-index file (malformed Release file?)

I cannot seem to find these entries in my sources.list.

Do you have any more suggestions how to fix this issue??

---

### Post by -=Ghost=- on 2009-06-05
Hey Plucky.

I commented out each 'deb-src' entry in my sources.list and this fixed the issue I was having.

I No longer have any error message when I update.

Thank-you for the help fixing my problem!

How Do I finish this my thread as solved?

---

### Post by plucky on 2009-06-05
> How Do I finish this my thread as solved? 

That feature has been removed from the forum,you could just add a "solved" tag at the bottom of the page.

Enjoy

---

### Post by -=Ghost=- on 2009-06-05
Okay I will do that.

I have just opened synapticpackage manager, and as soon as I opened it I got this error message:-

W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_i18n_Translation-en%5fGB)

I could still download and install the package I wanted (AWN Manager).

Can you shed any light on why I might be getting this new error messsage, and how I  ight be able to fix it??

---

### Post by plucky on 2009-06-05
Put a # in front of this line in your sources.list ```
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty restricted
``` which is just below the line in red in my previous post.

I think this might be the duplicate line.If not post the revised sources.list file.

---

### Post by -=Ghost=- on 2009-06-05
Plucky...

That sorted it..

Thank's again for helping me to fix my issue!

This Thread/Post is SOLVED by Plucky!

---


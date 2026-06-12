---
title: "Should I Upgrade to Firefox 1.0.4 or keep my FireFox 1.0.2???"
date: 2005-05-17
forum: Desktop Environments
---

### Post by FreeEagle on 2005-05-17
Hi all,

I have a question, my System is Up to date, But i have a question concerning FireFox, should i keep this 1.0.2 which come with the Ubuntu Distribution or Upgrade to the newst one 1.0.4, if yes what should i put in my Head when i Install Firefox 1.0.4 myself?
I did it for a friend of mine on his PC, because he asked me to do it for him, I will Write down here the way that i did as i installed Firefox form the tar Package.

1. Downloaded the tar from [www.Mozilla.org](www.Mozilla.org)
2. Loged as a root
3. Extacted the Package in the Root directory.
4. Started the Firefox installer by Double clicking on the Installer and then Changed the Path of the Directory to /usr/lib/mozilla-firefox , just kept the Old Directory name of the Old Firefox as it is, then Firefox will ask you if you want to delete the old Firefox and install the new one in the same folder, you should accept otherwise choose another directory.
5. Then I clicked on Next and thats all . 
6. done.

Then i installed for the first time Flash and Java. and other Programes.

But we recognized that there is just some Arabic Fonts looks little Different after the Installation, by using the Open source Fonts, so we decided to install M$ fonts, and everything work fine after that. 


The Question now!!!!
I do not want to Install M$ Fonts and just want to keep the Fonts that comes with my Ubuntu Hoary 5.04 , so what should i do in this case to make Firefox 1.0.4 just show me the same Fonts as my Firefox 1.0.2 did ?

Does anyone have any Suggestion accourding this HOwto? Have i missed somthing there to do ?

Please be free to Feedback me.

Best Regards,
 FreeEagle

---

### Post by neighborlee on 2005-05-17
[QUOTE=FreeEagle]Hi all,

I have a question, my System is Up to date, But i have a question concerning FireFox, should i keep this 1.0.2 which come with the Ubuntu Distribution or Upgrade to the newst one 1.0.4, if yes what should i put in my Head when i Install Firefox 1.0.4 myself?
I did it for a friend of mine on his PC, because he asked me to do it for him, I will Write down here the way that i did as i installed Firefox form the tar Package.

1. Downloaded the tar from [www.Mozilla.org](www.Mozilla.org)
2. Loged as a root
3. Extacted the Package in the Root directory.
4. Started the Firefox installer by Double clicking on the Installer and then Changed the Path of the Directory to /usr/lib/mozilla-firefox , just kept the Old Directory name of the Old Firefox as it is.
5. Then I clicked on Next and thats all . 
6. done.

Then i installed for the first time Flash and Java. and other Programes.

But we recognized that there is just some Arabic Fonts looks little Different after the Installation, by using the Open source Fonts, so we decided to install M$ fonts, and everything work fine after that. 


The Question now!!!!
I do not want to Install M$ Fonts and just want to keep the Fonts that comes with my Ubuntu Hoary 5.04 , so what should i do in this case to make Firefox 1.0.4 just show me the same Fonts as my Firefox 1.0.2 did ?

Does anyone have any Suggestion accourding this HOwto? Have i missed somthing there to do ?

Please be free to Feedback me.

Best Regards,
 FreeEagle[/QUOTE]
-----------
I have found most stable firefox is 1.0.3..1.0.4 drop down URL list is misbehaving that or its ubuntu i've no idea ( my nvidia problems )...if its not nvidia I def. dont reccommend going to 1.0.4..YMMV but that is what i'm seeing here in hoary and while this happened I looked at top and there were no run away apps ( spikes)

cheers
neighborlee

---

### Post by Julius on 2005-05-17
I think (not sure) that the bugfixes of Firefox 1.0.4 have been backported or something to hoary's 1.0.2. I'm not sure, but it would make sense since 1.0.4 was a crytical update.

Anyway, why don't you run both firefoxes and copy their font settings?

---

### Post by Rodrigo on 2005-05-17
[QUOTE=Julius]Anyway, why don't you run both firefoxes and copy their font settings?[/QUOTE]

hahaha  :grin: . NOW THAT'S a solution  ;-)

---

### Post by elsewhere on 2005-05-17
FWIW, 1.04 is in backports, I upgraded a couple of days ago with synaptic and am running without issues.  Didn't have to change my settings, theme etc., it kept it all.  Works like a charm.

Cheers,
KV

EDIT:  Here's [a link](http://www.ubuntuguide.org/#backportsrepositories) to the backports section in the Ubuntu Guide, in case you're interested in trying.

---

### Post by kyle01 on 2005-05-18
it seems as upgrading to 1.0.4 in some way is still the only way to get rid of this favicon vulnerability for example. The demo exploits still work with the latest official version 1.0.2-0ubuntu5.2
Perhaps I'm wrong here, but afaik
-this issue (and others ?) has been fixed in 1.0.4 about a week ago
-there is still no official fix for the ubuntu package
I am somehow disappointed about that.. I don't want to use an insecure browser for so long when there is an update available.

---

### Post by pja on 2005-05-19
There does not seem to be a 'deb' version of Firefox 1.0.4 yet and the Mozilla web site won't let you add extensions or themes unless you are running 1.0.4.

This prompted me to 'apt-get' **Opera** Version 8 and it works fine.

Regards,
Peter

---

### Post by christooss on 2005-05-20
[QUOTE=Gandalf]
if someone is still suffering from the problem that they can't visit firefox addons page here's the solution
go to about:config
search for general.useragent.vendorSub
change it from 1.0 to 1.0.4
and it should work

source : [https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)[/QUOTE]

This is workin perfectly

Post is from backports projeckt forum

---

### Post by FreeEagle on 2005-05-21
thansk all for your answers....


FreeEagle

---

### Post by nix4me on 2005-05-21
P*ss*s me off that Ubuntu hasn't kept up with the Firefox Release schedule.

---


---
title: "problem loading links from  kontact in firefox! please help!!"
date: 2005-09-23
forum: Desktop Environments
---

### Post by sal on 2005-09-23
i installed the firefox 1.0.7 package today (as per sudo apt-get upgrade) and now when i open a link from an email in Kontact, its opening it from the kdecache like this
file:///var/tmp/kdecache-samiam010203/krun/14422.0.

is what happens when i try and load this website

[http://sal-support.blogspot.com/](http://sal-support.blogspot.com/)

so what happens is when i click on the link [http://sal-support.blogspot.com/](http://sal-support.blogspot.com/) in the email a box pops up and then firefox loads and the address bar reads
file:///var/tmp/kdecache-samiam010203/krun/14422.0. 

instead of the real link.
what could be the cause of this?
please help me fix this. thanks in advance.

---

### Post by mlomker on 2005-09-23
> please help me fix this. thanks in advance.

I don't understand why this is a problem.  Is the correct web page getting loaded?  

The filename is displayed on the line because that is how the two programs are exchanging information.  You have to keep in mind that Firefox is a gnome application and Kontact is KDE.  I wouldn't be suprised if using a file was the best method for the two programs to 'talk' to each other.

---

### Post by sal on 2005-09-24
the websites are not loading. thats the problem.
for instance, when i got the email informing me that you had replied to the thread, i click on the link to the thread in kontact and firefox browser opens to a blank page and then dialog box pops up asking me if i want to open the php page in text editor or save it to disk.

the box that comes on the screen breefly before firefox loads, looks like the one you would see in ktorrent that transfers the download from the cache to the directory you are saving to. after that gos away then firefox opens to a blank page and then i get the firefox dialog box asking me if i want to open/save the file like i say above.

this only started to happen after i upgraded to firefox 1.0.7 yesterday following the NabsS method in this thread [http://ubuntuforums.org/showthread.php?t=68513](http://ubuntuforums.org/showthread.php?t=68513)

then after that now i have problems opening links from kontact emails.

---

### Post by mlomker on 2005-09-24
> this only started to happen after i upgraded to firefox 1.0.7 yesterday following the NabsS method in this thread [http://ubuntuforums.org/showthread.php?t=68513](http://ubuntuforums.org/showthread.php?t=68513)


I read the thread and, frankly, you should not have upgraded.  When packages have a different name (and you have to **--force** them to install) that is because they have not been adequately tested yet and released into the main repository.  

It looks like it has been re-released into the main repositories now.  If you are lucky you can run the system upgrade process today and it'll fix your problem, otherwise you may have to remove all of the firefox packages and then add them back.

---

### Post by sal on 2005-09-24
[QUOTE=mlomker]I read the thread and, frankly, you should not have upgraded.  When packages have a different name (and you have to **--force** them to install) that is because they have not been adequately tested yet and released into the main repository.  

It looks like it has been re-released into the main repositories now.  If you are lucky you can run the system upgrade process today and it'll fix your problem, otherwise you may have to remove all of the firefox packages and then add them back.[/QUOTE]

i just tryed a apt-get upgrade and no luck.
if i try to remove the packages in synaptic it wants to remove a lot of other stuff as well. i never had this problem before yesterday.
one thing of not, i have a firefox in /usr/bin and one in /usr/lib/mozilla-firefox/

should that be correct or is the /usr/lib/mozilla-firefox/ the newly named one from yesterday?

---

### Post by sal on 2005-09-24
ok got it fixed
here is what i had to do 
i had to replace the firefox command with mozilla-firefox %u in the app menu and on my short cuts to firefox then i went into kcontrol and set firefox as the default web browser and then i was able to load links from kontact in firefox with out any problems at all.

now that thats out of the way i can get back to enjoying ubuntu/kubuntu without banging my head against the monitor. ha ha.

---

### Post by mlomker on 2005-09-24
> i had to replace the firefox command with mozilla-firefox %u in the app menu and on my short cuts to firefox then i went into kcontrol and set firefox as the default web browser and then i was able to load links from kontact in firefox with out any problems at all.


Glad to hear it!  Now that you've reminded me, I did both of those things on the first day of my install but had forgotten about it.  I don't think the %U part is needed, but changing from firefox to mozilla-firefox is important.  I think what threw me with your question was that I don't use Kontact--I have web email.

---

### Post by mrowth on 2005-09-28
[QUOTE=mlomker]I don't understand why this is a problem.  Is the correct web page getting loaded?  

The filename is displayed on the line because that is how the two programs are exchanging information.  You have to keep in mind that Firefox is a gnome application and Kontact is KDE.  I wouldn't be suprised if using a file was the best method for the two programs to 'talk' to each other.[/QUOTE]

I've had the same problem with all-KDE apps instead of Firefox, though.

Click on a link in, say, Kmail, or in Kopete, and the "target" file is downloaded to /var/tmp/kdeacache-username/something-or-other and then opened as per a doubleclick from the file manager.

That is, clicking on [http://somewhere.org/something.jpeg](http://somewhere.org/something.jpeg) results in Gwenview showing me a local copy of the jpeg, and a webpage would likewise open as a local copy in Konqueror - all the relative URLs within are of course useless that way.

Making Firefox the "most preferred" application for HTML files somehow rectified that problem (for PHP pages as well) although the little dialogue box still pops up (but no mention of any cache)

Dunno what's going on there, links to images still open in Gwenview but no longer from cache...

Weirdness. But not too bad.

---

### Post by mrowth on 2005-09-28
However, clicking a link in a website in Konqueror now treats the target page like some random downloadable file:

> 
Open 'http://...whatever'?
Type: HTML Document

Save As... / Open with 'Firefox' / Cancel


*Sigh*

---

### Post by sal on 2005-09-28
[QUOTE=mlomker]Glad to hear it!  Now that you've reminded me, I did both of those things on the first day of my install but had forgotten about it.  I don't think the %U part is needed, but changing from firefox to mozilla-firefox is important.  I think what threw me with your question was that I don't use Kontact--I have web email.[/QUOTE]

yes, i use gmail, but im a traditionalist, i still like it to come in threw and actual program on my local system.

---


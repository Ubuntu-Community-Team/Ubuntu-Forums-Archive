---
title: "Windows Scribus not compatible with Ubuntu Scribus?"
date: 2006-07-07
forum: Desktop Environments
---

### Post by aysiu on 2006-07-07
I created a Scribus file in Windows XP at work (with a .sla extension). When I brought it home to Ubuntu Dapper, Scribus said it wasn't a valid .sla file.

Any ideas?

Is this standard? Could someone test it out? Could the file have somehow become corrupted by simply being copied to and from a USB key?

---

### Post by aysiu on 2006-07-08
This is the error message I get when I try to open in Ubuntu's Scribus the Windows-created Scribus file.

---

### Post by aysiu on 2006-07-10
Bump.

---

### Post by rykel on 2006-07-10
> **aysiu said:**
> I created a Scribus file in Windows XP at work (with a .sla extension). When I brought it home to Ubuntu Dapper, Scribus said it wasn't a valid .sla file.

Any ideas?

Is this standard? Could someone test it out? Could the file have somehow become corrupted by simply being copied to and from a USB key?

The error you see definitely seems to show that are some incompatibility problems between the two versions.

A simple way to test is to create more .sla documents in both versions and see if you face the same problem.

---

### Post by aysiu on 2006-07-10
I think I'll do that.

I hope it's just a fluke with that one file.

---

### Post by rykel on 2006-07-10
> **aysiu said:**
> I think I'll do that.

I hope it's just a fluke with that one file.

yeah, please do... i, for one, would like to know the result, as i am just beginning to learn how to do desktop publishing, and am reading up on adobe indesign, scribus etc.

on a related note, i believe ubuntu scribus has NOT been given some well-deserved attention, because when i first load some of the provided templates, fonts would have to be substituted, but usually by the first font on the system list.

that means some hindi or asian font, which is NOT the equivalent to the original fonts used in the template.

also, do you happen to know where i can download a pdf version of any recent scribus manual? thanks!!!

---

### Post by aysiu on 2006-07-10
I'm just beginning to explore Scribus myself. I'm no designer, but I do a lot of documentation--for work and for church--and sometimes word processors just don't keep things in the place you want them.

I had to reset the default font too to be something more Western (I use Bitstreamer Vera Roman).

---

### Post by aysiu on 2006-07-10
I tried it with two more files--no joy.

At first I thought it was a font thing, but I tried two files--one with Times New Roman, another with Bitstreamer Vera Roman. Neither worked.

Scribus isn't compatible with itself? What's up with that?

---

### Post by mikeoh on 2006-07-11
What are the versions of Scribus?

The file format has changed between the 1.2 releases and the 1.3 releases.  From the Scribus 1.3 help:
The file format has changed and is NOT backwardly compatible. You have been warned. We have specifically disabled the ability to open 1.3.x files in the stable 1.2.x versions. Our plans for a new file format should be settled in the 1.3.4 -1.3.5 development period.

I think the version in the Ubuntu is 1.2.4 but the latest release on the Scribus is 1.3.3

---

### Post by aysiu on 2006-07-11
Ah, thanks for that. I'm an idiot and didn't read.

My Windows version is 1.3.3.2, and my Ubuntu version is 1.2.4.1, so, yes... that would explain it.

Thanks again for pointing out what should have been obvious.

**Edit**: Okay. I read that page you quoted. But if 1.3.3.2 is not backwards compatible, does that mean 1.2.4.1 files won't work the other way around? If so, is there an easy way to convert them--through EPS export/import, maybe?

I'm a total beginner with desktop publishing, so bear with me.

---

### Post by bluenova on 2006-07-11
What's the version in Edgy? Perhaps we could get a backport to Dapper if it's 1.3.3.2.

---

### Post by hayesey on 2006-07-11
Installing "scribus-ng" (next generation) instead of "scribus" in Dapper should install 1.3.3.1-1.

---

### Post by aysiu on 2006-07-11
*scribus-ng* is available only in Edgy. I've already created some files in 1.2, though.

---

### Post by stig on 2006-07-11
Have you tried the Scribus mailing list for help with the compatibility of files? The people there are usually helpful and it's a close-knit community of DTPers. They can be a bit tetchy about criticism - but then who isn't! (They mostly have a good sense of humour and also many can respond in several languages.)

[http://nashi.altmuehlnet.de/mailman/listinfo/scribus](http://nashi.altmuehlnet.de/mailman/listinfo/scribus)

---

### Post by aysiu on 2006-07-11
Thanks for the suggestion, but I really have only one question, so joining a mailing list seems a bit extreme.

---

### Post by stig on 2006-07-11
> **aysiu said:**
> Thanks for the suggestion, but I really have only one question, so joining a mailing list seems a bit extreme.

I can understand that view but I think Scribus, like other DTP software, is more detailed and subtle than, say, word processors and there is more that one can learn from others. I recall that there is someone who is writing his own PDF manual and he sent me a draft of the section on importing files. Also, he was using regular expressions for changing quotes, for instance. Scribus is still in a relatively early stage of development and it's useful to have direct access to developers in the mailing list.

---

### Post by durand on 2007-01-12
Edit: Not Applicable now...
   bad post ](*,)
 .wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Verdana [microsoft]", "Lucida [B&h]", "Arial [monotype]", "Helvetica [Adobe]", "Arial [monotype]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }

---

### Post by danieljames on 2007-03-15
I found I could install the latest version of Scribus to Ubuntu by adding the following to the source lists at /etc/apt/sources.list

    deb [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) edgy main restricted
    deb [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) edgy main restricted

    deb-src [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) edgy main restricted
    deb-src [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) edgy main restricted

a key is available too but I think it is a good idea to read the instructions.  See the "Debian Repository w/Instructions" on the Scribus web site.  There  is specific information for buntu there.

They say that Scribus works better on Debian but I am having no problems.

---


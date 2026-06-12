---
title: "Evolution &amp; Spam"
date: 2006-07-19
forum: Desktop Environments
---

### Post by ColinG on 2006-07-19
I know this question must have been asked hundreds of times but how on earth do you get spam filtering in Evolution to work as effectively as that in Thunderbird (it even seems better under kde with Kmail).

I have tried the Bogofiter plugin. I am currently using using the  Spamassassin varient (which seems better) and have even tried both ](*,). Either way the results seem very poor and Thunderbird proves that baysian filters can be better than that. 

I'd move to Thunderbird immediately if it were not for the fact that there is no real calendering support yet - Lightning and Sunbird have a way to go.

Help would be appreciated gang :) 

Thanks
Colin

---

### Post by mrbaz on 2006-07-19
I thought there was a Baysian type filter for evolution?

---

### Post by ColinG on 2006-07-19
Bogofilter and Spamassassin give baysian support but it seems pretty ineffective to me. At least, it is when I compare with other implementations. I don't know if it is me or the way in which Evolution uses the plugins.

Colin

---

### Post by T700 on 2006-07-19
When I used Evolution, I ended up having to use the instructions on the Spam Assasian site to hand tweak the config file.  By default, it is VERY conservative.

Paul

---

### Post by ColinG on 2006-07-19
Do you happen to have the url, Paul, please. I could not find anything :( 

Incidentally, where does the config file reside?

Thanks
Colin

---

### Post by T700 on 2006-07-19
[Here you go]("http://spamassassin.taint.org/doc/Mail_SpamAssassin_Conf.html").  The link explains where the file resides and how to edit it.  It increased my hit rate to around 98%. 

Good luck,
Paul

---

### Post by ColinG on 2006-07-19
Tnaks mate, I'll get to it!

Did you set up any physical filters/rules within Evo or did you just rely on the plugin architecture. There seem to be differing opinions as to whether rules are needed or not

Thanks a mil
Colin :p

---

### Post by T700 on 2006-07-19
I just let it set up the filters for me and it seemed to sync nicely on its own.

Paul

---

### Post by ColinG on 2006-07-19
> **T700 said:**
> I just let it set up the filters for me and it seemed to sync nicely on its own.

Paul
There are no physical filters set-up in my Evolution. Not that I can see under edit...message filters

---

### Post by Riverside on 2006-07-29
> **ColinG said:**
> Bogofilter and Spamassassin give baysian support but it seems pretty ineffective to me.The SpamAssassin version packaged with Dapper (and the development branch, Edgy Eft, bizarrely) is hopelessly out of date:

[http://packages.ubuntu.com/dapper/mail/spamassassin](http://packages.ubuntu.com/dapper/mail/spamassassin)
[http://packages.ubuntu.com/edgy/mail/spamassassin](http://packages.ubuntu.com/edgy/mail/spamassassin)

SpamAssassin 3.1.0 was released on 14 September 2005, and has been superseded by more recent versions on 4 occasions since:

[http://spamassassin.apache.org/](http://spamassassin.apache.org/)

It really is frankly ridiculous to package a 10-month old version of SpamAssassin with a newly released distribution.  Due to the rapidity with which unscrupulous bulk emailers continually update and refine bulk email sending techniques, anything other than the latest release is likely to partly, or almost entirely, ineffective.

---


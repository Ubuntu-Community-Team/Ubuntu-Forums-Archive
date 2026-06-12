---
title: "Thunderbird won't launch Konqueror"
date: 2007-12-05
forum: Desktop Environments
---

### Post by pwaldo on 2007-12-05
Hi all,

I'm running Kubuntu Gutsy AMD64.  I can't seem to get Thunderbird to use Konqueror for hyperlinks.  It always wants to use FireFox.

In Thunderbird I have Edit|Preferences|Attachments set up so that HTML documents (.html, text/html) runs kfmclient.  I also tried "konqueror" here also.

I don't know whether it matters, but my KDE Defaults for the Web Browser is also "kfmclient".

Any help would be greatly appreciated!

Paul

---

### Post by vikram on 2007-12-05
I use Kmail and not Thunderbird so I haven't tried this but can you try and replace
"kfmclient" with

"kfmclient openURL" ?

---

### Post by pwaldo on 2007-12-05
> **vikram said:**
> I use Kmail and not Thunderbird so I haven't tried this but can you try and replace
"kfmclient" with

"kfmclient openURL" ?

Unfortunately, there is no place to enter a parameter; you can just pick an application via a file-selection dialog :-(

---

### Post by vikram on 2007-12-05
what happens if you create an alias ?

put this line in the profile. it is a hidden file in your home folder called .profile or .bash_profile or .bash_rc

alias kfmclient="kfmclient openURL"

---

### Post by pwaldo on 2007-12-06
> **vikram said:**
> what happens if you create an alias ?

put this line in the profile. it is a hidden file in your home folder called .profile or .bash_profile or .bash_rc

alias kfmclient="kfmclient openURL"

Thanks for the reply, Vikram.  No luck though.  Here is what I did
[HTML]$ alias kfmclient="`which kfmclient` openURL"

$ alias kfmclient
alias kfmclient='/usr/bin/kfmclient openURL'

$ thunderbird
[/HTML]
Thunderbird ran, but I still got the same result; URLs are opened in Firefox.

BTW, here is a data point that may or may not be helpful.  I think that thunderbird changed where preferences are stored at some point, as I have both a ~/.mozilla-thunderbird ~/.thunderbird directory.  Only one of these contains the settings to open Konqueror, though:
```
$ grep -r kfmclient ~/.mozilla-thunderbird/* ~/.thunderbird/*
/home/paul/.mozilla-thunderbird/691b5xg0.Paul Waldo/mimeTypes.rdf:
NC:path="/usr/bin/kfmclient" />

```
Could thunderbird be getting confused by the two?

---


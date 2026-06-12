---
title: "Still no sign of a Steam client?"
date: 2010-08-20
forum: Gaming &amp; Leisure
---

### Post by Cam! on 2010-08-20
It's been a while, and I'm starting to lose faith in Valve.

---

### Post by renkinjutsu on 2010-08-20
There has been NO official word from Valve.. Actually, the only "official" statement would be the one from this page [steampowered]("https://support.steampowered.com/kb_article.php?ref=1313-QIPD-5381").. and it's been up there since the beginning of time..

It's Phoronix that is bringing peoples' hopes up

---

### Post by Naiki Muliaina on 2010-08-20
Still no sign and tbh I hope it doesn't come to Linux.

Phronix should bury and remove their 'Steam is coming!' lines.

Some enterprising young fellow needs to make a new online app equivalent of Steam but better. Because Steam is not going to support Linux.

---

### Post by J.K.Makowka on 2010-08-20
In fact one of the big heads at Valve just recently stated in an interview that they are currently not working on a linux version (it sounded a bit like there has been some previous efforts which stated the rumors, and while there is currently no work done on it could be picked up sometime in the future again).

But personally I would not get my hopes up high, if it comes it would be nice, if not well not really that much of a problem.

---

### Post by alexandrius on 2010-08-21
> **Naiki Muliaina said:**
> Still no sign and tbh I hope it doesn't come to Linux.

Phronix should bury and remove their 'Steam is coming!' lines.

Some enterprising young fellow needs to make a new online app equivalent of Steam but better. Because Steam is not going to support Linux.

<snip>!

I'm sure that Valve will create steam for linux

---

### Post by V for Vincent on 2010-08-21
See the Linux thread on the Steam forums. There's been a very recent "we're not working on it" statement. I'm not saying it'll never be here, but, as of now, I hold more hopes for the software centre.

---

### Post by ELD on 2010-08-21
Phoronix started the rumors based on things that have been around for years (mentions of "linux" strings..they have been there for a long time). Then pictures of a half-assed client (no way near finished) and he even said a date "June" which has long passed.

He did it to get my clicks on his ads, nothing more...move along!!

---

### Post by Naiki Muliaina on 2010-08-21
Aside from Phoronix are there any references (pref recent ones...) that say Steam is coming to Linux?

---

### Post by ELD on 2010-08-21
> **Naiki Muliaina said:**
> Aside from Phoronix are there any references (pref recent ones...) that say Steam is coming to Linux?

Nothing apart from members of valve stating its not happening.

---

### Post by Sutekh849 on 2010-08-21
they would have said that no matter what: deny until official announcement is valve's standard tactic.
the incomplete pre alpha at one point downloadable from the official steam website from 
here [http://store.steampowered.com/public/client/steam_client_linux](http://store.steampowered.com/public/client/steam_client_linux)
a link that _still_ gives a 403 error because *something *is there, but not accessible. will it ever be completed and released? i don't know. but they *are* at least thinking about it or they would not be hosting an in development version on their website, and although phoronix typically overhyped the whole thing, there is some truth in what they reported.

EDIT  new news (heh)
a file found in the recent beta of CS:S (counterstrike source)
hl2.sh

>     #!/bin/bash
     
    # figure out the absolute path to the script being run a bit
    # non-obvious, the ${0%/*} pulls the path out of $0, cd's into the
    # specified directory, then uses $PWD to figure out where that
    # directory lives - and all this in a subshell, so we don't affect
    # $PWD
     
    GAMEROOT=$(cd "${0%/*}" && echo $PWD)
     
    #determine platform
    UNAME=`uname`
    if [ "$UNAME" == "Darwin" ]; then
       # prepend our lib path to LD_LIBRARY_PATH
       export DYLD_LIBRARY_PATH="${GAMEROOT}"/bin:$DYLD_LIBRARY_PATH
    elif [ "$UNAME" == "**Linux**" ]; then
       # prepend our lib path to LD_LIBRARY_PATH
       export LD_LIBRARY_PATH="${GAMEROOT}"/bin:$LD_LIBRARY_PATH
    fi
     
    if [ -z $GAMEEXE ]; then
      GAMEEXE=hl2_osx
    fi
     
    ulimit -n 2048
     
    # and launch the game
    cd "$GAMEROOT"
     
    STATUS=42
    while [ $STATUS -eq 42 ]; do
        ${DEBUGGER} "${GAMEROOT}"/${GAMEEXE} "$@"
        STATUS=$?
    done
    exit $STATUS

---

### Post by Naiki Muliaina on 2010-08-21
Phoronix made it sound like a Linux client was about to be released. The best we have is an invisible pre alpha build and steam announcing they are not working on a Linux client? Too over hyped. Until Valve announce a steam client, I cant see any reason for the plethora of 'Is steam here yet?' threads. 

Heres hoping Steam doesn't come to Linux and an industrious young fellow makes something better.

---

### Post by donkyhotay on 2010-08-21
> **Cam! said:**
> It's been a while, and I'm starting to lose faith in Valve.

They're just making certain they get it right. It'll take some time but it'll be worth it. Just ask all the fans waiting for Duke Nukem Forever... oh wait...
</sarcasm>

I've said it before, I'll say it again. At best it's vaporware, and thats being generous. I'd classify steam on linux as rumorware. I won't believe steam will be available for linux until the day *after* the official client is available for download on the official valve site. Even then I wouldn't care because I never liked steam on windows and wouldn't use it on linux.

---

### Post by alexandrius on 2010-08-22
just left the hope for Ubuntu Software Store

---

### Post by Naiki Muliaina on 2010-08-22
> **alexandrius said:**
> just left the hope for Ubuntu Software Store

Still hope some industrious young fellow will think of a good way to make money from a Linux games portal. :) Its a big world with lots of Linux users and devs. If there is real money to be made there, someone will exploit the little niche.

---


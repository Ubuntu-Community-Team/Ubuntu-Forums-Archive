---
title: "Easy plugin question I hope  =)"
date: 2006-07-25
forum: Desktop Environments
---

### Post by XeroCurve on 2006-07-25
I upgraded to dapper and now am still working on the Mplayer plugin issue. The sound will still not play in Firefox but at least now I have the correct plugins in this directory:

/usr/lib/firefox/plugins

but they are not in this directory:

/opt/firefox/plugins

Do I need to copy them into this directory also?

---

### Post by taurus on 2006-07-25
Use a symlink then...

```

sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins

```

---

### Post by XeroCurve on 2006-07-25
Thanks for the suggestion but the sound will still not play. I thought this would be an easy thing to do but its turning out to be a nightmare. All I need is a little "DING" to play on a website and I cant get it to work. Its hard to sell ubuntu when I cant get a simple little ding to play as an alert.

I know its a plugin issue because the sound works fine on other things. In fact this is the only problem ive had, but its a make or break point for the function its going be used for. If I cant get it to work then I have to reinstall Winblows. Please help! I will provide any system information you need.

---

### Post by taurus on 2006-07-25
How did you install that mplayer plugins?  I recommand you use Automatix to install all the media plugins for your machine.  Then, you will hear more than just a DING!!!

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by cantormath on 2006-07-25
> **XeroCurve said:**
> I upgraded to dapper and now am still working on the Mplayer plugin issue. The sound will still not play in Firefox but at least now I have the correct plugins in this directory:

/usr/lib/firefox/plugins

but they are not in this directory:

/opt/firefox/plugins

Do I need to copy them into this directory also?

Use Automatix. It does it all for you.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)
just install the codec and plugins through automatix and it will set it up for you.

---

### Post by XeroCurve on 2006-07-25
Automatix is what I used. I used this thread:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by XeroCurve on 2006-07-25
OK, I have installed Automatix and then I tried to install Mplayer and plugins through it and Firefox will still not play sounds in browser. All people keep telling me is to use Automatix or EasyUbuntu which for me it appears is not Automatic or Easy. Are there other suggestions, or maybe im missing something very basic that I havent done?

---

### Post by avtolle on 2006-07-25
Perhaps we are confused about what is wanted to happen. As I understand the Original Poster, the desire is for there to be "a ding" when a certain web site is opened in FF. Thus, could it be he/she is really looking for a FF extension, and not the app itself? For, it appears, Mplayer has been installed through Automatix, and the desired behavior is not occurring. So, I ask that the OP restate what is the desired behavior, TIA.

---

### Post by XeroCurve on 2006-07-25
Well I guess im wanting embedded sounds in webpages to play. I tried the Websters website test with the pronunciations and firefox states in the pop up bar that the there are plugins that are needed.

---

### Post by cantormath on 2006-08-01
> **XeroCurve said:**
> Well I guess im wanting embedded sounds in webpages to play. I tried the Websters website test with the pronunciations and firefox states in the pop up bar that the there are plugins that are needed.

automatix or easy ubuntu should do it, if you are still having problems, it should not be codec problem with firefox.  with automatix, try swiftfox and the plugins.
Also install the AUD-CODECS
MPLAYER & FF PLUGINS (FF =FIREFOX)
and give opera a try, its cool.

---


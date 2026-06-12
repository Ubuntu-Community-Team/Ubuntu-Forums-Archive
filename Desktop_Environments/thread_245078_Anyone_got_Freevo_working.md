---
title: "Anyone got Freevo working?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by megamaced on 2006-08-27
Hello

I've got Freevo installed sucessfully via unofficial repositories, but I haven't been able to watch TV yet. Can anyone give me some tips or perhaps point me to a tutorial?

Thanks

---

### Post by mcpish on 2006-08-29
I've just installed it and it's working perfectly on my 27" Sony Trinitron TV.

To properly install it on Ubuntu Dapper Drake just add this entry to your /etc/apt/sources.list file
> 
deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) dapper universe multiverse


Then enter
> 
wget [http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg](http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg)
sudo apt-key add geole.info-apt-key.gpg


then type 
> 
sudo apt-get install freevo


To get it to work properly in Ubuntu, after you have it installed, you need to enter in these 2 lines to the bottom of your **~/.freevo/local_conf.py** file:
> 
CONFIG_VERSION = 5.15
MPLAYER_VERSION = 0.9


Then execute "freevo" from the command line.  There are also a ton of other options and settings you can configure in the local_conf.py file.

If you are using an nvidia-card with TV output, you should definatly set the TVoverscan option to get rid of any black border around the whole screen by editing your **~/.nvidia-settings-rc** file with the overscan setting and then having n**vidia-settings --load-config-only** execute when X starts-up.

---

### Post by megamaced on 2006-08-29
Cool, so far so good.

But the other problem I had was getting XMLTV working. I am in the UK so I am using tv_grab_uk_rt but it's horribily out of date! Even the new version from the CVS is out of date

Anyway, I tried to grab the TV listings using the command freevo tv_grab but I got an error. I can't remember exactly what it said.

How did you set up XMLTV to work with Freevo?

In fact, would you mind posting your local_config.py file here because that'd give me a much better idea

---


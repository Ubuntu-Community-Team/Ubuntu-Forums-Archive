---
title: "Default sans font?"
date: 2011-01-25
forum: Desktop Environments
---

### Post by khughitt on 2011-01-25
Hi all,

I'm trying to figure out what fonts "sans", etc map to. After reading [this thread]("http://ubuntuforums.org/showthread.php?t=652269")
I was able to find /etc/fonts/conf.d/60-latin.conf which specifies:

```

<alias>
	<family>sans-serif</family>
	<prefer>
		<family>DejaVu Sans</family>
		<family>Bitstream Vera Sans</family>
		<family>Verdana</family>
		<family>Arial</family>
		<family>Albany AMT</family>
		<family>Luxi Sans</family>
		<family>Nimbus Sans L</family>
		<family>Helvetica</family>
		<family>Lucida Sans Unicode</family>
		<family>BPG Glaho International</family> <!-- lat,cyr,arab,geor -->
		<family>Tahoma</family> <!-- lat,cyr,greek,heb,arab,thai -->
	</prefer>
</alias>

```

So it looks like "DejaVu Sans" is the preferred font *family* when "sans" is specified. There are many different styles of DejaVu Sans, however, such as "extra light", "condensed", etc. I tried to find a definition of where the DejaVu Sans family is defined, but have not had any luck.

I'm running Ubuntu 10.04 with Gnome now, and I know the default fonts have changed in 10.10, but I imagine the basic method for mapping fonts is still the same.

Any suggestions?

Thanks,

---

### Post by pascaltch on 2011-01-25
hello,

for be frank, i haven't any clue for your problem but i have seen my question  just below than your question and i waiting an answer me too , it's first time for me to ask a question under licence by-nc-nd !
what is your licence cc by , cc-nc .....?
sincerely

---

### Post by miklcct on 2011-01-26
I tried using Kubuntu 10.10 and found that the 'default' font had been changed to 'Ubuntu'. However, when I studied these configuration files, I found no difference. After that, I played with System Settings and clicked the "Default" button under the font settings, it reverts to Sans Serif. After that, I was surprised that the 'default' font was changed by a nasty inclusion to the kubuntu-default-settings folder in some configuration file.

---


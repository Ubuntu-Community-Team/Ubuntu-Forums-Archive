---
title: "yahoo games"
date: 2006-07-17
forum: Gaming &amp; Leisure
---

### Post by papafred07 on 2006-07-17
hello everyone!
I have just finished making the transition from windows to ubuntu and am already enjoying it.  I've been trying to get yahoo games functioning so that I can play yahoo chess.  Right now, whenever I click to play now, this pops up, "Yahoo! Chess requires Flash Player 7 or later and JavaScript enabled in your browser."  I surfed around these forums and found numerous different options for solving this.  However, I was unable to make any of these function.  Any help would be appreciated.
Thanks

---

### Post by Jagot on 2006-07-17
[https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)
[https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e](https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e)

---

### Post by eqisow on 2006-07-17
```
sudo apt-get install sun-java5-jre sun-java5-plugin flashplugin-nonfree
```

You will need extra repositories enabled to do this. See [here]("https://help.ubuntu.com/community/Repositories") for help with that.

After you get those things installed, restart Firefox and go to about:plugins in the address bar. You should see "Java(TM) Plug-in 1.5.0_06-b05" and "Shockwave Flash" listed.

---

### Post by Perfect Storm on 2006-07-17
Manually:

Download Java from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
to your Desktop.

Close your browser(s), to the terminal, batman ;)

```
cd Desktop
tar -zxf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer

```

When you see this:
> Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

type: **/usr/lib/mozilla-firefox**

Done.

Now you need install the fonts that flash needs:

```
sudo apt-get install gsfonts-x11
sudo fc-cache -f -v

```

Done.

---

### Post by Eddie Wilson on 2006-07-17
You can also use Automatrix to install whats needed. That worked for me now I can play Yahoo spades.

---

### Post by GetJef on 2010-02-27
Hello, 

I encountered the same issue and simply used my **Ubuntu Software Center** to *install* **Sun Java 6.0 Plugin**.  Just type in **Java** and it should display the most current plugin.  Once installed, *restart* your Firefox.  This worked for me.

Thanks,
GetJef ;)

---


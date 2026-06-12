---
title: "Ugly fonts on UTF-8 encoded Chinese webpages, etc."
date: 2006-06-04
forum: Desktop Environments
---

### Post by elian on 2006-06-04
After installing Dapper and then installing Chinese support, I can view a UTF-8 encoded Chinese webpage using Firefox and its default settings. All characters are present, but the characters are a wierd mixture of different Chinese fonts and slightly different sizes. I've attached a small 18 kb portion of a screenshot to show the problem.

How can I fix this? (I noticed the same problem in Breezy.)

---

### Post by ki1022 on 2006-06-04
Well, I dont know chinese....but it looks like any other chinese fonts i've seen.

---

### Post by Rondonjin on 2006-06-04
[QUOTE=elian]After installing Dapper and then installing Chinese support, I can view a UTF-8 encoded Chinese webpage using Firefox and its default settings. All characters are present, but the characters are a wierd mixture of different Chinese fonts and slightly different sizes. I've attached a small 18 kb portion of a screenshot to show the problem.

How can I fix this? (I noticed the same problem in Breezy.)[/QUOTE]

Japanese fonts are bad too, even with the tips in another thread on how to improve font rendering in Dapper. The height of the Chinese characters and Hiragana/Katakana are all bad and bold fonts are really ugly. I switched over to a Japanese desktop and took a screenshot, it's really bad. Strangely, DBCS fonts were better in FC5 but I much prefer Ubuntu.

[http://www.ubuntuforums.org/showthre...ght=howto+font](http://www.ubuntuforums.org/showthre...ght=howto+font)

[http://www.ubuntuforums.org/showthre...highlight=font](http://www.ubuntuforums.org/showthre...highlight=font)

Wayne

---

### Post by linuxa on 2006-06-04
[QUOTE=Rondonjin]Japanese fonts are bad too, even with the tips in another thread on how to improve font rendering in Dapper. The height of the Chinese characters and Hiragana/Katakana are all bad and bold fonts are really ugly. I switched over to a Japanese desktop and took a screenshot, it's really bad. Strangely, DBCS fonts were better in FC5 but I much prefer Ubuntu.

[http://www.ubuntuforums.org/showthre...ght=howto+font](http://www.ubuntuforums.org/showthre...ght=howto+font)

[http://www.ubuntuforums.org/showthre...highlight=font](http://www.ubuntuforums.org/showthre...highlight=font)

Wayne[/QUOTE]


What kind of font are you guys using?

Default font that came with Kubuntu Dapper - AR PL SunHeiSan Uni seems to be fine here.

I've also had success with firefly font in the past. Search this forum for a link to the download and instruction for installation.

I've had no problems with either font when browsing or as the default font for the entire desktop.

---

### Post by elian on 2006-06-04
I'm just using whatever the defaults were, after installing Dapper, the Chinese language packs, and easyubuntu. The out-of-box defaults aren't good for this combo... is this an issue with the font server config? I can't see why Firefox would be switching from one font to another on it's own accord...

How do I set the default fonts on a system wide basis?

---

### Post by linuxa on 2006-06-05
[QUOTE=elian]I'm just using whatever the defaults were, after installing Dapper, the Chinese language packs, and easyubuntu. The out-of-box defaults aren't good for this combo... is this an issue with the font server config? I can't see why Firefox would be switching from one font to another on it's own accord...

How do I set the default fonts on a system wide basis?[/QUOTE]

Not too sure for Ubuntu, look for something like system settings. Then font or appearance after that. You should know that this will only change the font for Desktop, there are separate font controls for Konquereor & whatever web browser that you are using. You should however at least notice the change in font of the characters appearing in your toolbar for the browser window (assuming you've got a foreign language page open).

For Kubuntu 6.06, it's KMenu -> System Settings -> Appearance -> Font.

Click the button that allows you to change all of the fonts at once. And select something begining with AR PL (for Chinese this is right I think). See screenshot.
This would exclude the fixed width font I think, so change that if you need to.

For Konqueor, Under Settings -> Konqueror settings. The Font setting governs the web browsing fonts. Under appearance there's another font that determines what font to use for folder names and such. Equivalent font controls should exist for whatever application you are using (e.g. Nautilus, Firefox, etc).

Good luck.

---

### Post by shawnling on 2006-06-05
[QUOTE=elian]After installing Dapper and then installing Chinese support, I can view a UTF-8 encoded Chinese webpage using Firefox and its default settings. All characters are present, but the characters are a wierd mixture of different Chinese fonts and slightly different sizes. I've attached a small 18 kb portion of a screenshot to show the problem.

How can I fix this? (I noticed the same problem in Breezy.)[/QUOTE]
why dont you go to the chinese forum to try your luck?
[http://forum.ubuntu.org.cn/](http://forum.ubuntu.org.cn/)
there are tons of discussion over chinese fonts

---

### Post by simosx on 2006-06-06
[QUOTE=shawnling]why dont you go to the chinese forum to try your luck?
[http://forum.ubuntu.org.cn/](http://forum.ubuntu.org.cn/)
there are tons of discussion over chinese fonts[/QUOTE]

Most probably it's FreeSans that's messing about CJK.
Try to remove the Freefont package and check again.

---

### Post by elian on 2006-12-21
> **linuxa said:**
> 
Default font that came with Kubuntu Dapper - AR PL SunHeiSan Uni seems to be fine here.

I've also had success with firefly font in the past. Search this forum for a link to the download and instruction for installation.


Aha! Telling Firefox to use AR PL SunHeiSan Uni instead of the default Serif fixes this! Thanks!

---

### Post by enjahova on 2007-02-21
I'm using Edgy with GNOME. I have this same problem, but I don't find it feasible to just switch to a Chinese font for all my text, as it makes western text hard to read. How can I make ubuntu handle Chinese better system wide? This is a problem in firefox and gaim. Why does it mix up different fonts/sizes for different characters?

I was going to try removing ttf-freefonts, but it said ubuntu-desktop depends on it... is this a problem?

---

### Post by ophion on 2007-02-21
> **enjahova said:**
> I'm using Edgy with GNOME. I have this same problem, but I don't find it feasible to just switch to a Chinese font for all my text, as it makes western text hard to read. How can I make ubuntu handle Chinese better system wide? This is a problem in firefox and gaim. Why does it mix up different fonts/sizes for different characters?

I was going to try removing ttf-freefonts, but it said ubuntu-desktop depends on it... is this a problem?

I am having the same problem and would also appreciate a real solution.

---

### Post by cisforcojo on 2007-03-06
I am having the same problem as well. Really really annoying. Changing the font in Firefox changes the fonts for the entire screen and that makes it hard to read. Any help would be greatly appreciated! I'm currently looking up how to disable anti-aliasing.

---

### Post by cisforcojo on 2007-03-06
I just now solved this problem!

You should (don't have to) install the firefly font. Google it. It's cleaner and does look better.
Then you need to disable antialiasing.

I had to create a file called .fonts.conf and place it in my home directory.

Here is what the file looks like:
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- Disable font alias for Chinese <= 16px -->
  <match target="font">
    <test qual="any" name="family" compare="eq">
      <string>AR PL Mingti2L Big5</string>
      <string>AR PL SungtiL Big5</string>
      <string>AR PL New Sung</string>
      <string>AR PL ShanHeiSun Uni</string>
      <string>AR PL ZenKai Uni</string>
      <string>Ming(ISO10646)</string>
      <string>MingLiu</string>
      <string>PMingLiu</string>
      <string>Kochi Mincho</string>
      <string>Baekmuk Dotum</string>
    </test>
    <test name="pixelsize" compare="less_eq">
      <double>16</double>
    </test>
    <edit name="antialias">
      <bool>false</bool>
    </edit>
    <edit name="hinting">
      <bool>true</bool>
    </edit>
  </match> 
  <alias>
      <family>serif</family>
      <prefer>
         <family>Bitstream Vera Serif</family>
         <family>Times New Roman</family>
         <family>Times</family>
	 <family>AR PL New Sung</family>
         <family>AR PL ShanHeiSun Uni</family>
	 <family>AR PL Mingti2L Big5</family>
	 <family>AR PL SungtiL GB</family>
	 <family>SimSun</family>
      </prefer>
  </alias>
   <alias>
      <family>sans-serif</family>
      <prefer>
         <family>Bitstream Vera Sans</family>
	 <family>Arial</family>
	 <family>Verdana</family>
	 <family>Helvetica</family>
	 <family>AR PL New Sung</family>
         <family>AR PL ShanHeiSun Uni</family>
	 <family>AR PL kaitiM Big5</family>
	 <family>AR PL kaitiM GB</family>
      </prefer>
  </alias>
  <alias>
      <family>monospace</family>
      <prefer>
         <family>Bitstream Vera Sans Mono</family>
	 <family>Courier New</family>
	 <family>Courier</family>
	 <family>AR PL New Sung</family>
         <family>AR PL ShanHeiSun Uni</family>
      </prefer>
  </alias>
</fontconfig>


The fonts are no longer blurry and mismatched. This worked for the whole system, firefox, everything. Let me know if you have any problems.

---

### Post by supersandy on 2008-03-05
I have removed all the japanese font, and now it looks pretty good for me.

---

### Post by fdimmling on 2008-03-07
> **supersandy said:**
> I have removed all the japanese font, and now it looks pretty good for me.
Actually you should remove all East-Asian fonts except for the Chinese, if you only need Chinese. I have installed the Bitstream Cyberbit font in addition to get uniformly good looking Chinese traditional and simplified characters. 
AFAIK the problem is that the first suitable font in alphabetical order is used when a Chinese characters has to be displayed. In the original Ubuntu installation this is a Japanese font which does not contain all Chinese characters. Thus, maybe later on other fonts have to be used in additin which gives a nonuniform picture. 

Friedrich

---


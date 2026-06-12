---
title: "Applets and desktop effects disabled after changing font settings"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by icelemontea on 2007-11-03
hi!:)
I just made some changes to allow the system to display Chinese fonts properly. On restarting Xwindows, the fonts work well, but some of the applets on the panel fail to launch and worst of all, my desktop effects cannot be enabled!!

What I did was:
1) copy some fonts to /usr/share/fonts/zh_CN/TrueType/
2)```
sudo chmod 644 /usr/share/fonts/zh_CN/TrueType/*
cd /usr/share/fonts/zh_CN/TrueType/
sudo mkfontscale
sudo mkfontdir
sudo fc-cache /usr/share/fonts/zh_CN/TrueType/

```
3)change /etc/fonts/language-selector.conf to
```
<fontconfig>
        <alias>
                <family>serif</family>
                <prefer>
                        <family>Bitstream Vera Serif</family>
                        <family>SimSun</family>
                        <family>DejaVu Serif</family>
                        <family>AR PL ShanHeiSun Uni</family>
                        <family>AR PL ZenKai Uni</family>
                </prefer>
        </alias>
        <alias>
                <family>sans-serif</family>
                <prefer>
                        <family>Bitstream Vera Sans</family>
                        <family>SimSun</family>
                        <family>DejaVu Sans</family>
                        <family>AR PL ShanHeiSun Uni</family>
                        <family>AR PL ZenKai Uni</family>
                </prefer>
        </alias>
        <alias>
                <family>monospace</family>
                <prefer>
                        <family>Bitstream Vera Sans Mono</family>
                        <family>DejaVu Sans Mono</family>
                        <family>SimSun</family>
                </prefer>
        </alias>
        <match target="font" >
                <test name="family" compare="contains" >
                        <string>Song</string>
                        <string>Sun</string>
                        <string>Kai</string>
                        <string>Ming</string>
                </test>
                <test compare="more_eq" target="pattern" name="weight" >
                        <int>180</int>
                </test>
                <edit mode="assign" name="embolden" >
                        <bool>true</bool>
                </edit>
        </match>
        <match target="font" >
                <test name="family" compare="contains" >
                        <string>Song</string>
                        <string>Sun</string>
                        <string>Kai</string>
                        <string>Ming</string>
                </test>
                <edit name="globaladvance">
                        <bool>false</bool>
                </edit>
                <edit name="spacing">
                        <int>0</int>
                </edit>
                <edit name="hinting">
                        <bool>true</bool>
                </edit>
                <edit name="autohint">
                        <bool>false</bool>
                </edit>
                <edit name="antialias" mode="assign">
                        <bool>true</bool>
                </edit>
                <test name="pixelsize" compare="less_eq">
                        <int>18</int>
                </test>
                <edit name="antialias" mode="assign" >
                        <bool>false</bool>
                </edit>
        </match>
       <match target="pattern">
              <test name="family">
                     <string>SimSun</string>
                     <string>SimSun-18030</string>
                     <string>AR PL ShanHeiSun Uni</string>
                     <string>AR PL New Sung</string>
                     <string>MingLiU</string>
                     <string>PMingLiU</string>
              </test>
              <edit binding="strong" mode="prepend" name="family">
                     <string>Tahoma</string>
                     <string>Verdana</string>
              </edit>
       </match>
        <match target="pattern">
              <test name="family"><string>&#23435;&#20307;</string></test>
              <edit name="family" mode="assign"><string>SimSun</string></edit>
       </match>
       <match target="pattern">
              <test name="family"><string>&#26032;&#23435;&#20307;</string></test>
              <edit name="family" mode="assign"><string>SimSun</string></edit>
       </match>
       <match target="pattern">
              <test name="family"><string>&#20223;&#23435;_GB2312</string></test>
              <edit name="family" mode="assign"><string>FangSong_GB2312</string></edit>
       </match>
       <match target="pattern">
              <test name="family"><string>&#26999;&#20307;_GB2312</string></test>
              <edit name="family" mode="assign"><string>KaiTi_GB2312</string></edit>
       </match>
       <match target="pattern">
              <test name="family"><string>&#40657;&#20307;</string></test>
              <edit name="family" mode="assign"><string>SimHei</string></edit>
       </match>
</fontconfig>
```
4)change font settings from the preference menu
5)```
sudo fontconfig-voodoo -f -s zh_CN
```

Can anyone kindly help me figure out what went wrong?
Or is there any way that I can undo a change to the system?
Sorry if this is sort of basic knowledge...I'm quite a newbie. Any help will be greatly appreciated.:)

---


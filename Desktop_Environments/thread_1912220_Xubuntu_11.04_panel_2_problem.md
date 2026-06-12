---
title: "Xubuntu 11.04 panel 2 problem"
date: 2012-01-20
forum: Desktop Environments
---

### Post by Conte77 on 2012-01-20
I accidentally deleted all the icons from the panel 2! Can someone who is using Xubuntu 11.04 send me picture with list of default itemes? I want picture like [that]("http://www.google.me/imgres?q=xubuntu+11.04+panel+1+items&um=1&hl=sr&client=ubuntu&channel=cs&biw=1024&bih=681&tbm=isch&tbnid=A4ADtpDfYBHx-M:&imgrefurl=http://xflinux.blogspot.com/2011/02/xubuntu-1104-review-and-first-look.html&docid=0MMJeNevVXZaYM&imgurl=http://4.bp.blogspot.com/_lSjTnDFuZ2k/TUw2L1H55LI/AAAAAAAAAHw/vnJWK37JM14/s1600/Xubuntu%252B11.04%252BAlpha2%252B%25252528Snapshot%252B1%25252529%252B%2525255BRunning%2525255D%252B-%252BOracle%252BVM%252BVirtualBox_019.png&w=1026&h=836&ei=K1IZT7HoNsWBtQabxOBH&zoom=1&iact=hc&vpx=493&vpy=352&dur=4311&hovh=203&hovw=249&tx=65&ty=172&sig=115196602054708523013&page=2&tbnh=159&tbnw=195&start=12&ndsp=16&ved=1t:429,r:6,s:12"), but for panel 2 :)
I hope to get a quick response :D

---

### Post by Toz on 2012-01-20
Hello and welcome to the forums.

In the event you don't get an 11.04 user to respond, you can find this information in the /etc/xdg/xdg-xubuntu/xfce4/panel/default.xml file. Its a little confusing, but search for "showdesktop" (which is the first one). The others will follow. For 11.10, it looks like this:
```

    <property name="plugin-11" type="string" value="[COLOR="Red"]showdesktop[/COLOR]"/>
    <property name="plugin-12" type="string" value="[COLOR="Red"]separator[/COLOR]">
      <property name="style" type="uint" value="1"/>
    </property>
    <property name="plugin-13" type="string" value="launcher">
      <property name="items" type="array">
        <value type="string" value="[COLOR="Red"]exo-web-browser.desktop[/COLOR]"/>
      </property>
    </property>
    <property name="plugin-14" type="string" value="launcher">
      <property name="items" type="array">
        <value type="string" value="[COLOR="Red"]exo-mail-reader.desktop[/COLOR]"/>
      </property>
    </property>
    <property name="plugin-15" type="string" value="launcher">
      <property name="items" type="array">
        <value type="string" value="[COLOR="Red"]exo-terminal-emulator.desktop[/COLOR]"/>
      </property>
    </property>
    <property name="plugin-16" type="string" value="launcher">
      <property name="items" type="array">
        <value type="string" value="[COLOR="Red"]xfce-settings-manager.desktop[/COLOR]"/>
      </property>
    </property>
    <property name="plugin-17" type="string" value="launcher">
      <property name="items" type="array">
        <value type="string" value="[COLOR="Red"]xfce4-appfinder.desktop[/COLOR]"/>
      </property>
    </property>
.....etc,etc,etc

```

---


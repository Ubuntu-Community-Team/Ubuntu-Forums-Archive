---
title: "HOWTO:  Quick Fix Indicator Plugin"
date: 2011-12-04
forum: Desktop Environments
---

### Post by MaquinaX on 2011-12-04
Hello Everyone,

      The reason why I decided to create this thread was because during these last day I was having a really tough time with my basic Xubuntu indicators (Mail, Volume, Network, Load)..... My basic issue is that somehow..., my mail and volume indicators disappeared. My network indicator somehow survived, but would have a hard time connecting, and then would suddenly crash, and disappear. I went through several threads, which suggested to uninstall and then reinstall indicator plugins, and the corresponding applets. Also, there was another one which suggested to delete the panel configs, and then replace them with those in
/etc/xfce4/, or something similar. I looked over the configs on:
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

and as you can see, nothing out of the ordinary that can cause conflict.

```

      <property name="plugin-4" type="string" value="systray">
      <property name="show-frame" type="bool" value="false"/>
      <property name="size-max" type="uint" value="22"/>
      <property name="names-visible" type="array">
        <value type="string" value="thunar"/>
        <value type="string" value="networkmanager applet"/>
        <value type="string" value="task manager"/>
        <value type="string" value="blueman-applet"/>
        <value type="string" value="vmware-tray"/>
        <value type="string" value="xfce4-power-manager"/>
        <value type="string" value="multiload"/>
        <value type="string" value="notes"/>
        <value type="string" value="swt"/>
      </property>

```
       Now the next part I must have gone through about 100 times, but I guess there is nothing out of the ordinary, if you don't know what you're looking for, right??? So right click on any empty portion of the panel, go down to the "panel>" option, and another window will pull-out. Choose "panel preferences" and a panel option window will pop-up. Click on the 
"Items" tab:
[IMG]http://i48.photobucket.com/albums/f231/MaquinaX/Panel-1.png[/IMG]

       I you look down to the 4th item, "Indicator Plugin" was missing completely in my case. So just click "Add" or the "+" sign, and it will
bring up another window with items that you want to add. If you also somehow lost your indicator plugin, go ahead and add it, and all your indicators will once again re-appear. Another option can also be to remove it from the panel items, and then re-adding it. My Indicators have now been restored to my Panel, and working as should be:
[IMG]http://i48.photobucket.com/albums/f231/MaquinaX/Indicators.png[/IMG]

Hopes this help at least one lost soul, to avoid the frustration that I had to go through. Good luck to everyone.                      :lolflag:

MaquinaX

---

### Post by Dogmudgeon on 2012-06-12
It helped THIS lost soul, MaquinaX ... Thanks!

(That makes one bug swatted, a hundred more to go.) 

):P

---


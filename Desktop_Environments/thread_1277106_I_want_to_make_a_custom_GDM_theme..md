---
title: "I want to make a custom GDM theme."
date: 2009-09-27
forum: Desktop Environments
---

### Post by CastilleV on 2009-09-27
I really want to make my own custom one, but I don't quite know how.

Is there a tutorial? I couldn't find one on the wiki.

And can anyone explain this to me?

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE greeter SYSTEM "greeter.dtd">
<greeter>

  <!-- background -->
  <item type="pixmap">
    <normal file="background.png"/>
    <pos y="0" x="0" width="100%" height="100%"/>
  </item>

  <!-- bottom bar -->
  <item type="pixmap">
     <normal file="bottom_bar.svg"/>
    <pos y="100%" x="0" width="100%" height="100" anchor="sw"/>
  </item>
  <item type="rect">
    <pos y="100%" x="0" width="100%" height="42" anchor="sw"/>
    <box xpadding="10" spacing="10" orientation="horizontal">
      <!-- options -->
      <item type="rect" id="options_button" button="true">
        <pos y="50%" width="box" height="box" anchor="w"/>
        <box xpadding="0" spacing="2" orientation="horizontal">
          <item type="pixmap">
            <normal file="icon-session.png"/>
            <prelight file="icon-session-prelight.png"/>
            <active file="icon-session-active.png"/>
          </item>
          <item type="label">
            <normal font="Sans 11" color="#ffffff"/>
            <prelight font="Sans 11" color="#ff9c36"/>
            <active font="Sans 11" color="#dc292b"/>
            <pos y="50%" anchor="w"/>
            <stock type="options"/>
          </item>
        </box>
      </item>
    </box>
  </item>
  
  <!-- hostname and clock -->
  <item type="rect">
    <pos x="100%" y="100%" width="box" height="42" anchor="se"/>
    <box xpadding="10" spacing="10" orientation="horizontal">
      <item type="label" id="clock">
        <pos x="100%" y="50%" anchor="e"/>
        <normal font="Sans 11" color="#ffffff"/>
        <text>%c</text>
      </item>
    </box>
  </item>
  
  
  <!-- password box -->
  <item type="rect">
    <pos x="50%" y="47%" width="box" height="box" anchor="c"/>
        <box xpadding="0" ypadding="0" spacing="0" orientation="vertical">
	<item type="pixmap">
	<pos x="0" y="0" width="box" height="box"/>
	<normal file="boundingbox.png"/>
	<box xpadding="40" ypadding="20" spacing="2" orientation="vertical"> 
          <item type="label" id="pam-prompt">
            <pos x="2"/>
            <normal font="Sans 12" color="#ffffff"/>
            <stock type="username-label"/>
          </item>
          <item type="pixmap">
            <normal file="userentry.png"/>
            <pos width="240" height="32"/>
            <fixed>
              <item type="entry" id="user-pw-entry">
		<normal color="#000000" font="Sans 11"/>
                <pos y="5" x="5" width="-10" height="-10" anchor="nw"/>
              </item>

<!-- caps lock warning -->
  <item type="label" id="caps-lock-warning">
<pos x="270" y="11" anchor="nw"/>
    <normal font="Sans 11" color="#ffffff"/>
    <stock type="caps-lock-warning"/>
  </item>
  <!-- timer warning -->
  <item type="label" id="timed-label">
    <pos x="50%" y="84" anchor="c"/>
    <show type="timed"/>
    <normal font="Sans 11" color="#ffffff"/>
    <stock type="timed-label"/>
  </item>
  <!-- pam error -->
  <item type="label" id="pam-error">
    <pos x="50%" y="120" width="290" anchor="c" />
    <normal font="Sans 11" color="#ff9c36"/><!--#dc292b-->
    <text></text>
  </item>
</fixed>            
          </item>
        </box>
      </item>
      <item type="rect">
        <box xpadding="10" ypadding="8" spacing="10" orientation="horizontal" homogeneous="true">
          <!-- language -->
          <item type="rect" id="language_button" button="true">
          </item>
          <!-- session -->
          <item type="rect" id="session_button" button="true">
          </item>
        </box>
  </item>
</box>
</item>
<!-- pam message (hidden, but required) -->
<item type="label" id="pam-message">
  <pos x="50%" anchor="c" />
  <normal alpha="0.00"/>
  <text></text>
</item>

</greeter>

```

---

### Post by Lars Noodén on 2009-09-28
Here is some documentation for KDM:
[http://docs.kde.org/stable/en/kdebase-workspace/kdm/kdm-themes.html](http://docs.kde.org/stable/en/kdebase-workspace/kdm/kdm-themes.html)

It's (maybe) not quite the same, but there is significant overlap betweem XDM, KDM, and GDM.  Anyway, that should give material to help refine your search for GDM documentation.

---

### Post by VCoolio on 2009-09-28
Pick one you more or less like from /usr/share/gdm/themes or from gnome-look.org, extract on your desktop and tweak. You can of course just replace the pictures, but the xml file is where everything is configured. [This]("http://blog.dipinkrishna.info/2009/06/howto-create-your-own-gdm-themes.html") seems a good howto, only I can't recommend using vi for text editing, make that nano in terminal or just gedit. 

You can install gdmthemetester to see what your theme is going to look like without having to install it and logout. Also [this post]("http://ubuntuforums.org/showpost.php?p=7576112&postcount=365") has some useful things. 

Don't invest too much in it: as far as I've understood gdm is not used in karmic or at least not themeable.

---

### Post by paradj on 2009-10-27
> I really want to make my own custom one, but I don't quite know how.

Is there a tutorial? I couldn't find one on the wiki.

And can anyone explain this to me?



not sure if you've found any help here but you could try this site

[http://live.gnome.org/GnomeArt/Tutorials/GdmThemes]("http://live.gnome.org/GnomeArt/Tutorials/GdmThemes")

personally i like this feature and im not sure as to why gdmgreeter is not going to be available in future releases as no one has given a concise and understandable answer to this for me.:confused:  so for now due not only to physical, and, financial restrictions;:-({|= i have to stick with intrepid. and too i would appreciate a gui to set the dialog boxes size and placement on the greeter as all the XML wysiwyg editors i've tried do not handle the greeter language well...so for that im still searchin]](*,)

---


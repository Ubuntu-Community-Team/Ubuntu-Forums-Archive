---
title: "login screen font size problem"
date: 2007-02-17
forum: Desktop Environments
---

### Post by Edocecrous on 2007-02-17
Hello!

I'll need some help on the following: Where does ubuntu keeps which font to use on the login screen?

Here's some pictures of my problem (that is the font size is huge):

This supposed to be CS:
[IMG]http://www.mynergy.com/ebay/gnome1.jpg[/IMG]

And this is the menu at the lower left corner:
[IMG]http://www.mynergy.com/ebay/gnome2.jpg[/IMG]

:confused:

---

### Post by Spin Doctor on 2007-02-17
> 
I'll need some help on the following: Where does ubuntu keeps which font to use on the login screen?I believe you find this info in the human.xml Try edit this file:```
gksu nautilus
go to: /usr/share/gdm/themes/Human
```Make a backup first of the xml file, just in case =)

---

### Post by Edocecrous on 2007-02-18
Thanx!

Found the xml, and fixed up the font size for the login/password. The menu didn't change thoug, but after some digging, i found it in the gtk folder, and now that's fixed too.

Thank you again!

Csaba
(directx/win32 system programmer - linux nooby)
:)

---

### Post by mbabbe on 2007-02-25
I am having the exact same problem. But when I edit Human.xml the sizes all appear to be properly set.   File permissions are 666, so should be okay.   

I'm a newbie, am I missing something.


  <!-- password box -->
  <item type="rect">
    <pos x="50%" y="60%" width="box" height="box" anchor="c"/>
    <box xpadding="0" ypadding="0" spacing="5" orientation="vertical">
      <item type="rect">
        <pos x="0" y="0" width="box" height="box" expand="true"/>
        <normal color="#ffffff" alpha="0.15"/>
        <box xpadding="50" ypadding="15" spacing="10" orientation="vertical">
          <item type="label" id="pam-prompt">
            <pos x="0"/>
            <normal font=[COLOR="Blue"]"Bitstream Vera Sans Bold 10"[/COLOR] color="#523921"/>
            <stock type="username-label"/>
          </item>
          <item type="rect">
            <normal color="#523921"/>
            <pos width="160" height="24"/>
            <fixed>
              <item type="entry" id="user-pw-entry">
		<normal color="#000000" font=[COLOR="Blue"]"Bitstream Vera Sans Bold 10"[/COLOR]/>
                <pos y="1" x="1" width="-2" height="-2" anchor="nw"/>
              </item>
            </fixed>
          </item>
          <!-- timer warning -->
          <item type="label" id="timed-label">
            <show type="timed"/>
            <normal font=[COLOR="Blue"]"Bitstream Vera Sans Bold 11"[/COLOR] color="#523921"/>
            <stock type="timed-label"/>
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

---

### Post by xmas1888 on 2007-04-06
Hey Edocecrous, what did you change in GTK to fix this?

---


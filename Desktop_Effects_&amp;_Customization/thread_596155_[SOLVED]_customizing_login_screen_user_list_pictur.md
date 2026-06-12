---
title: "[SOLVED] customizing login screen user list picture"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by soumo on 2007-10-29
Hi folks,

I have recently added a bunch of themes to the GDM login and had them working fine.

I decided to tinker with them but haven't found a lot (any) support instructions.  Basically I was able to figure out how to add a userlist to any theme (just by cutting and pasting the code:

[COLOR="Red"]<!-- liste des utilisateurs -->

  <item type="rect">
    
    <normal color="#171f7b"/>
    <pos anchor="c" x="25%" y="50%" height="box" width="box"/>
    <box orientation="vertical" min-width="250" max-width="300" xpadding="4" ypadding="4" height="550" spacing="0">
      <item type="rect">
	<normal color="#e9d193"/>
        <pos anchor="n" x="50%" height="378" width="378"/>
	<fixed>
          <item type="list" id="userlist">
            <pos anchor="nw" x="1" y="1" height="-2" width="-2"/>
          </item>
	</fixed>
      </item>
    </box>
  </item>
[/COLOR]

& inserting 

[COLOR="#ff0000"]<item type="label" id="pam-prompt">
        <pos x="0"/>
        <normal font="Bitstream Vera Sans Bold 9" color="#523921"/>
        <stock type="username-label"/>
</item>
[/COLOR]

this as well before it asks for the password, from a theme that already has the user list into one that doesn't (found in /usr/share/gdm/themes).

Now what I'd like to do is to make the user picture larger.  I have used up to 145x145 pixels in the .face file saved as a PNG file with no difficulties.  After that, the picture becomes a generic silhouette.  I have played with the numbers in the user code above to no avail.  I tried using an xml editor (xml mind) but I cannot open the file as it states, the file cannot be opened as it can't find greeter.dtd. 

The only help I was able to search out on the net or here was:
[http://ubuntuforums.org/showthread.php?t=535138&highlight=edit+user+list+login+screen](http://ubuntuforums.org/showthread.php?t=535138&highlight=edit+user+list+login+screen)

but it didn't help.

So can anyone please explain the coding to me or at least where I can get some more help?

-Thanks in advance,
 Soumo.

---

### Post by soumo on 2007-10-29
Also I have a slightly bizarre issue with Kiba dock now reserving the bottom strip of my screen for itself after these changes!  Basically I see a black strip running across the bottom (2 fingers width of a 15.4" screen), which can reveal only the dock, or the auto-hidden taskbar from the gnome desktop.  Quiting the dock repairs this.  This is not a huge issue yet, but I'm uncertain why this would happen?

---

### Post by soumo on 2007-10-30
Found a great tutorial here if anyone is interested:
[http://www.5z.com/jirka/gdm-documentation/x1259.html](http://www.5z.com/jirka/gdm-documentation/x1259.html)

The Kiba dock prob is partly solved by unchecking the always on top option...

---


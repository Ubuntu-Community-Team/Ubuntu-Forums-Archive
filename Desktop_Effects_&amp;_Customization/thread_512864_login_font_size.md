---
title: "login font size"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by jbnc on 2007-07-29
My login font size is overly large for the box where you type in the username and password. I think it may have been caused after the installation of the nvidia drivers. My screen resolution is 1920 x 1200. Is there any way I can adjust the font size there? My font otherwise is the correct size though.

---

### Post by pandion on 2007-07-30
Hi,

If your login greeter screen resolution is the size that you want (this will affect the font size appearance), you can manually change the font size by editing the *.XML file associated with the Greeter Theme that you're using (the location depends on whether you're using Gnome/KDE/XFCE etc.).  The Font and the Font Size are specified in this file, along with the size and location of the text box you type your ID and password in etc.  Hope this helps!

---

### Post by jbnc on 2007-07-30
when I open the xml file I cant seem to figure out which line to edit to change the font size within the box. Could you explain to me which line I would edit  plz?

---

### Post by jbnc on 2007-07-30
Also when I connect it to an external monitor it looks perfectly fine at 1024 x 768 :S i'm so confused..

---

### Post by pandion on 2007-07-31
Post the XML file text here so I can take a look at it.  They all vary a bit..

---

### Post by jbnc on 2007-08-05
<?xml version="1.0"?>
<!DOCTYPE greeter SYSTEM "greeter.dtd">

<greeter>

  <!-- first we take care of the background stuff -->
  <item type="rect">
    <normal color="#cccccc"/>
    <pos x="0" y="0" width="100%" height="100%"/>
  </item>

  <item type="pixmap">
    <normal file="background.jpeg" alpha="1"/>
    <pos x="0" y="0" width="100%" height="100%"/>
  </item>
  
  <!-- the hostname and clock on topright -->
  <item type="label" id="clock">
    <normal color="#ffffff" font="Sans 10" alpha="0.8"/>
    <pos x="-20" y="22" anchor="e"/>
    <text>%c</text>
  </item>
  <item type="label" id="hostname">
    <normal color="#ffffff" font="Sans 10" alpha="0.8"/>
    <pos x="-20" y="42" anchor="e"/>
    <text>%h</text>
  </item>

  
  <item type="rect" id="timed-rect">
    <show type="timed"/>
    <normal color="#FFFFFF" alpha="0.1"/>
    <pos anchor="c" x="50%" y="65%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label" id="timed-label">
        <normal color="#ffffff" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
	<!-- Stock label for: User %s will login in %d seconds -->
	<stock type="timed-label"/>
      </item>
    </box>
  </item>

  <item type="rect">
    <!-- just put our foot in the middle as a reference point for the rest -->
    <pos anchor="center"  x="30%" y="35%"/>
    <fixed>

    <item type="pixmap">
      <normal file="shade-left.png" alpha="0.08"/>
      <pos x="-300" y="-25" width="25%" height="51" anchor="ne"/>
    </item>

    <!-- Behind Foot -->
    <item type="rect">
      <normal color="#eeeeec" alpha="0.6"/>
      <pos x="-300" y="-25" width="80" height="51" anchor="nw"/>
    </item>

    <!-- Behind GNOME Desktop -->
    <item type="rect">
      <normal color="#666664" alpha="0.3"/>
      <pos x="-220" y="-25" width="180" height="51" anchor="nw"/>
    </item>

    <!-- Behind Input -->
    <item type="rect">
      <normal color="#eeeeec" alpha="0.6"/>
      <pos x="-40" y="-25" width="320" height="51" anchor="nw"/>
    </item>

    <item type="pixmap">
      <normal file="shade-right.png" alpha="0.08"/>
      <pos x="280" y="-25" width="25%" height="51" anchor="nw"/>
    </item>

    <item type="pixmap">
      <normal file="dotline.png" alpha="0.6"/>
      <pos anchor="center" width="3200" height="1" x="0" y="-25"/>
    </item>

    <item type="pixmap">
      <normal file="dotline.png" alpha="0.6"/>
      <pos anchor="center" width="3200" height="1" x="0" y="25"/>
    </item>

     <item type="pixmap">
       <normal file="small-n.png" alpha="1"/>
       <pos anchor="center" x="-260" y="0"/>
     </item>

        <item type="pixmap">
          <normal file="gnome-linux-desktop.png" alpha="1"/>
          <pos anchor="center" x="-115" y="0"/>
        </item>
<!-- inp -->
     <item type="rect">
        <pos anchor="center" x="-30" y="0" width="box" height="box"/>
          <box orientation="horizontal" spacing="3">
            <item type="rect">
              <!-- web designer trick - a spacer cell! ;-) -->
              <pos width="310" height="20" x="0" y="0"/>
            </item>
            <item type="label" id="pam-prompt">
                <pos anchor="w" y="50%"/>
	        <normal color="#000000" font="Sans 10"/>
		<stock type="username-label"/>
	    </item>
            <item type="rect">
              <pos anchor="w" height="20" width="140" y="50%" expand="false"/>
                <fixed>
  	          <item type="entry" id="user-pw-entry">
                    <normal color="#000000" font="Sans 9"/>
                    <pos anchor="nw" x="6" y="1" height="-1" width="-8"/>
	          </item>
              </fixed>
            </item>
          </box>
        </item>


  <!-- session/language/disconnect buttons -->
    <item type="rect">
    <!-- the parent is hidden, but it just puts us on the correct place
         in relation to the loginbox - then we offset from it -->         
      <pos anchor="s" y="36" x="-46"/>
      <box orientation="horizontal" xpadding="12" spacing="12" homogenous="false" >
	  <item type="label" id="language_button">
	    <normal color="#eeeeee" alpha="0.9" font="Sans 10"/>
	    <prelight color="#ffffff" alpha="1" font="Sans 10"/>
	    <active color="#dddddd" alpha="0.9" font="Sans 10"/>
	    <stock type="language"/>
	  </item>

          <item type="svg">
            <normal file="vline.svg"/>
            <pos width="10" height="30"/>
          </item>

	  <item type="label" id="session_button">
	    <normal color="#eeeeee" alpha="0.9" font="Sans 10"/>
	    <prelight color="#ffffff" alpha="1" font="Sans 10"/>
	    <active color="#dddddd" alpha="0.9" font="Sans 10"/>
	    <stock type="session"/>
	  </item>

          <item type="svg">
	    <show modes="console" type="system"/>
            <normal file="vline.svg"/>
            <pos anchor="nw" width="10" height="30"/>
          </item>

	  <item type="label" id="system_button" button="true">
	    <show modes="console" type="system"/>
	    <normal color="#eeeeee" alpha="0.9" font="Sans 10"/>
	    <prelight color="#ffffff" alpha="1" font="Sans 10"/>
	    <active color="#dddddd" alpha="0.9" font="Sans 10"/>
	    <stock type="system"/>
	  </item>

      <!-- OR -->

          <item type="svg">
   	    <show modes="remote"/>
            <normal file="vline.svg"/>
            <pos anchor="nw" width="10" height="30"/>
          </item>

	  <item type="label" id="disconnect_button">
	    <normal color="#eeeeee" alpha="0.9" font="Sans 10"/>
	    <prelight color="#ffffff" alpha="1" font="Sans 10"/>
	    <active color="#dddddd" alpha="0.9" font="Sans 10"/>
	    <stock type="disconnect"/>
	    <show modes="remote"/>
	  </item>

          <item type="svg">
   	    <show modes="flexi"/>
            <normal file="vline.svg"/>
            <pos anchor="nw" width="10" height="30"/>
          </item>

	  <item type="label" id="disconnect_button">
	    <normal color="#eeeeee" alpha="0.9" font="Sans 10"/>
	    <prelight color="#ffffff" alpha="1" font="Sans 10"/>
	    <active color="#dddddd" alpha="0.9" font="Sans 10"/>
	    <stock type="quit"/>
	    <show modes="flexi"/>
	  </item>

    </box>
    </item>
    </fixed>
  </item>

  <item type="rect" id="caps-lock-warning">
    <normal color="#eeeeee" alpha="0.1"/>
    <pos anchor="c" x="50%" y="28%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label">
        <normal color="#eeeeee" font="Sans 14"/>
        <pos x="50%" anchor="n"/>
        <stock type="caps-lock-warning"/>
      </item>
      <item type="label">
        <normal color="#eeeeee" font="Sans 10"/>
        <pos x="50%" anchor="n"/>
        <text>Passwords and usernames are case-sensitive</text>
      </item>
    </box>
  </item>

  <item type="rect" id="pam-error">
    <pos anchor="c" x="70%" y="34%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label" id="pam-error">
        <normal color="#eeeeee" font="Sans 10"/>
        <pos x="70%" anchor="n"/>
        <text/>
      </item>
    </box>
  </item>

</greeter>

---

### Post by pandion on 2007-08-07
The lines that have Font=Sans ##" are where the Font and Font Size are specified.  As for the Login Text Box, this is different from others I've seen and looks like it has a timed prompt for the User ID (not certain, just guessing based on the syntax).  You can tell what each section is for based on the "Type". 

<item type="rect" id="timed-rect">
<show type="timed"/>
<normal color="#FFFFFF" alpha="0.1"/>
<pos anchor="c" x="50%" y="65%" width="box" height="box"/>
<box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
<item type="label" id="timed-label">
<normal color="#ffffff" font="Sans 12"/>                                                       **(This looks like the Font line for the ID input box)**
<pos x="50%" anchor="n"/>
<!-- Stock label for: User %s will login in %d seconds -->
<stock type="timed-label"/>
</item>
</box>
</item>

**Try changing "Sans 12" to another font size (such as "Sans 10" etc.) to see see if it's the one that affects the Font size of the User ID text box.**

<item type="pixmap">
<normal file="gnome-linux-desktop.png" alpha="1"/>
<pos anchor="center" x="-115" y="0"/>
</item>
<!-- inp -->
<item type="rect">
<pos anchor="center" x="-30" y="0" width="box" height="box"/>
<box orientation="horizontal" spacing="3">
<item type="rect">
<!-- web designer trick - a spacer cell! -->
<pos width="310" height="20" x="0" y="0"/>
</item>
<item type="label" id="pam-prompt">
<pos anchor="w" y="50%"/>
<normal color="#000000" font="Sans 10"/>
<stock type="username-label"/>
</item>
<item type="rect">
<pos anchor="w" height="20" width="140" y="50%" expand="false"/>
<fixed>
<item type="entry" id="user-pw-entry">
<normal color="#000000" font="Sans 9"/>                                                       **(This looks like the Font line for the Password input box)**
<pos anchor="nw" x="6" y="1" height="-1" width="-8"/>
</item>
</fixed>
</item>
</box>
</item>

**Then try changing "Sans 9" to another font size (such as "Sans 10" to keep the ID and Password text size the same) to see see if it's the one that affects the Font size of the Password text box.  It looks like "Sans 10" is being used for most of the text in this Greeter.  Since it looks like the ID text is set to "Sans 12" and the Password text is set to "Sans 9", it would of course make them look different size wise.  Since yours may be too large a Font for what you want, you may want to change them to "Sans 8" or another smaller size instead**.

Just make a backup copy of the XML file before you start making changes so you can switch it back if there's a problem, and so you have a reference as to what the original was.  What is the name of this Greeter (it looks like a GNOME Greeter), and is it a standard Ubuntu Greeter or one you added?  I would have to play around with the XML file to be sure those are the right places to change the fonts you want to change.

Another potential issue is that your Login Greeter may actually be getting displayed at a different resolution than what you have your Desktop set to.  If you can move the mouse around to the edges of the screen and the Login image moves/slides around, then it is being displayed at a larger resolution (which would also make the Fonts look over-sized).  Checkout my posts on this thread ([http://ubuntuforums.org/showthread.php?t=498922&page=4](http://ubuntuforums.org/showthread.php?t=498922&page=4)) if it's actually a Login Greeter resolution issue.

Hope this helps!

---


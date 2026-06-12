---
title: "Double click on GDM login photo doesn't work"
date: 2005-10-13
forum: Desktop Environments
---

### Post by byoon on 2005-10-13
Double clicking on my GDM login photo doesn't work properly anymore.

On Hoary:
Single click - it used to put my username into the username input space
Double click - it used to put my username into the username input space and send a return so that it then prompted me for my password

On Breezy:
Single click - it puts my username into the username input space
Double click - it puts my username into the username input space but DOESN'T send a return so that I need to manually hit return on the keyboard

I am using a modified CleanLinux GDM theme from gnome-look.org.  Here is my configuration file:

> 
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE greeter SYSTEM "greeter.dtd">
<greeter>
  <!-- papier peint http://www.gnome-look.org/content/files/15888-Blue-Steel-Clean.jpg-->
  <item type="pixmap">
    <normal file="cleanlinux.png"/>
    <pos x="0" y="0" width="100%" height="100%"/>
  </item>

  <item type="rect">
    <normal color="#ffffff" alpha="0.5" />
    <pos anchor="c" x="50%" y="69%" width="532" height="320"/>

    <box orientation="horizontal" spacing="10" xpadding="15" ypadding="15">

      <!-- selecteur -->
      <item type="list" id="userlist">
        <pos width="246" height="290"/>
      </item>


      <!-- liste verticale -->
      <item type="rect">
        <pos width="246" height="290"/>
        <box orientation="vertical" spacing="10">

          <!-- Bienvenue -->
          <item type="label">
            <pos anchor="n" x="50%" width="box"/>
            <normal color="#000000" font="Sans 32"/>
            <stock type="welcome-label"/>
          </item>

          <!-- horloge -->
          <item type="label" id="clock">
            <normal color="#000000" font="Sans 12"/>
            <pos anchor="n" x="50%"/>
            <text>%c</text>
          </item>

          <!-- message -->
          <item type="label" id="pam-prompt">
            <pos anchor="n" x="50%"/>
            <normal color="#000088" font="Sans 14"/>
            <stock type="username-label"/>
          </item>

          <!-- champ -->
          <item type="entry" id="user-pw-entry">
            <pos anchor="n" x="50%" height="24" width="192"/>
          </item>

          <!-- erreur -->
          <item type="label" id="pam-error">
            <pos anchor="n" x="50%"/>
            <normal color="#880000" font="Sans 12"/>
            <text/>
          </item>

          <!-- boutons -->
          <item type="rect">
            <pos anchor="n" x="50%" y="100%" width="box" height="box"/>
            <box orientation="horizontal" spacing="0" xpadding="5">

              <!-- langue -->
              <item type="rect" id="language_button" button="true">
                <pos width="box" height="box"/>
                <box orientation="vertical" spacing="0" xpadding="5">
                  <item type="pixmap">
                    <normal file="langue.png" tint="#dddddd"/>
                    <prelight file="langue.png"/>
                    <active file="langue.png" tint="#ff0000"/>
                    <pos x="50%" anchor="n"/>
                  </item>
                  <item type="label">
                    <normal color="#000000" font="Sans 12"/>
                    <prelight color="#666666" font="Sans 12"/>
                    <active color="#ff0000" font="Sans 12"/>
                    <pos x="50%" anchor="n"/>
                    <stock type="language"/>
                  </item>
                </box>
              </item>

              <!-- session -->
              <item type="rect" id="session_button" button="true">
                <pos width="box" height="box"/>
                <box orientation="vertical" spacing="0" xpadding="5">
                  <item type="pixmap">
                    <normal file="session.png" tint="#dddddd"/>
                    <prelight file="session.png"/>
                    <active file="session.png" tint="#ff0000"/>
                    <pos x="50%" anchor="n"/>
                  </item>
                  <item type="label">
                    <normal color="#000000" font="Sans 12"/>
                    <prelight color="#666666" font="Sans 12"/>
                    <active color="#ff0000" font="Sans 12"/>
                    <pos x="50%" anchor="n"/>
                    <stock type="session"/>
                  </item>
                </box>
              </item>

              <!-- actions -->
              <item type="rect" id="system_button" button="true">
                <show modes="console" type="system"/>
                <pos width="box" height="box"/>
                <box orientation="vertical" spacing="0" xpadding="5">
                  <item type="pixmap">
                    <normal file="actions.png" tint="#dddddd"/>
                    <prelight file="actions.png"/>
                    <active file="actions.png" tint="#ff0000"/>
                    <pos x="50%" anchor="n"/>
                  </item>
                  <item type="label">
                    <normal color="#000000" font="Sans 12"/>
                    <prelight color="#666666" font="Sans 12"/>
                    <active color="#ff0000" font="Sans 12"/>
                    <pos x="50%" anchor="n"/>
                    <stock type="system"/>
                  </item>
                </box>
              </item>

              <!-- deconnecter -->
              <item type="rect" id="disconnect_button" button="true">
                <show modes="flexi,remote"/>
                <pos width="box" height="box"/>
                <box orientation="vertical" spacing="0" xpadding="5">
                  <item type="pixmap">
                    <normal file="quitter.png" tint="#dddddd"/>
                    <prelight file="quitter.png"/>
                    <active file="quitter.png" tint="#ff0000"/>
                    <pos x="50%" anchor="n"/>
                  </item>
                  <item type="label">
                    <normal color="#000000" font="Sans 12"/>
                    <prelight color="#666666" font="Sans 12"/>
                    <active color="#ff0000" font="Sans 12"/>
                    <pos x="50%" anchor="n"/>
                    <stock type="disconnect"/>
                    <show modes="remote"/>
                  </item>
                  <item type="label">
                    <normal color="#000000" font="Sans 12"/>
                    <prelight color="#666666" font="Sans 12"/>
                    <active color="#ff0000" font="Sans 12"/>
                    <pos x="50%" anchor="n"/>
                    <stock type="quit"/>
                    <show modes="flexi"/>
                  </item>
                </box>
              </item>

            </box><!-- liste des boutons -->
          </item>

        </box><!-- liste de droite -->
      </item>

    </box><!-- liste horizontale -->
  </item>





  <item type="rect" id="caps-lock-warning">
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="50%" y="85%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label">
        <normal color="#000000" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
        <!-- Stock label for: You've got capslock on! -->
        <stock type="caps-lock-warning"/>
      </item>
    </box>
  </item>

  <item type="rect">
    <show type="timed"/>
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="75%" y="25%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label" id="timed-label">
        <normal color="#000000" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
        <!-- Stock label for: User %s will login in %d seconds -->
        <stock type="timed-label"/>
      </item>
    </box>
  </item>

</greeter>


---


---
title: "HOWTO: Edit Live CD Panels Position , Contents , Size , etc"
date: 2009-01-17
forum: Desktop Environments
---

### Post by ermali86 on 2009-01-17
[COLOR="Black"][B]======================
Introduction
======================[/B][/COLOR]

Hello to all. 

**[COLOR="Red"]Read Carefully Below :[/COLOR]**

- First at all i am sorry if someone has posted this before but i searched and didn't found it.

- This is my first how to so any help , advise , idea or judgement will be appreciated.

- I am not going to explain how to edit a Live CD because that is well written here : [**[COLOR="Black"]LiveCDCustomization[/COLOR]**]("https://help.ubuntu.com/community/LiveCDCustomization")



**I wanted to change the Live CD Gnome Panels because i am Customizing the Ubuntu CD for some people that are familiar with windows so i wanted to change the panels position so they look like windows and attract them more to Ubuntu. Don't misunderstand me. I don't want to make Ubuntu look like windows. I just want to make more people use it.**


[B][COLOR="Black"]======================
Work Done
======================[/COLOR][/B]

**1.** When you are in **CHROOT** in the Live CD edit this file :

```
nano /etc/gconf/schemas/panel-default-setup.entries
```

I use nano but you can vim or another editor if you like.


**2.** The original file that i had was this :

```
<gconfentryfile>

  <entrylist base="/apps/panel/default_setup">

    <!-- List of toplevels -->

    <entry>
      <key>general/toplevel_id_list</key>
      <schema_key>/schemas/apps/panel/general/toplevel_id_list</schema_key>
      <value>
        <list type="string">
          <value>
            <string>top_panel</string>
          </value>
          <value>
            <string>bottom_panel</string>
          </value>
        </list>
      </value>
    </entry>

    <!-- List of objects -->

    <entry>
      <key>general/object_id_list</key>
      <schema_key>/schemas/apps/panel/general/object_id_list</schema_key>
      <value>
        <list type="string">
          <value>
            <string>menu_bar</string>
          </value>
          <value>
            <string>browser_launcher</string>
          </value>
          <value>
            <string>email_launcher</string>
          </value>
          <value>
            <string>yelp_launcher</string>
          </value>
          <value>
            <string>clock_separator</string>
          </value>
        </list>
      </value>
    </entry>

    <!-- List of applets -->

    <entry>
      <key>general/applet_id_list</key>
      <schema_key>/schemas/apps/panel/general/applet_id_list</schema_key>
      <value>
        <list type="string">
          <value>
            <string>mixer</string>
          </value>
          <value>
            <string>clock</string>
          </value>
          <value>
            <string>notification_area</string>
          </value>
          <value>
            <string>show_desktop_button</string>
          </value>
          <value>
            <string>window_list</string>
          </value>
          <value>
            <string>workspace_switcher</string>
          </value>
          <value>
            <string>trashapplet</string>
          </value>
          <value>
            <string>fast_user_switch</string>
          </value>
        </list>
      </value>
    </entry>

  <!-- Top Panel -->

    <entry>
      <key>toplevels/top_panel/expand</key>
      <schema_key>/schemas/apps/panel/toplevels/expand</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/disable_movement</key>
      <schema_key>/schemas/apps/panel/toplevels/disable_movement</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/orientation</key>
      <schema_key>/schemas/apps/panel/toplevels/orientation</schema_key>
      <value>
        <string>top</string>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/size</key>
      <schema_key>/schemas/apps/panel/toplevels/size</schema_key>
      <value>
        <int>24</int>
      </value>
    </entry>

    <entry><key>toplevels/top_panel/name</key><schema_key>/schemas/apps/panel/toplevels/name</schema_key></entry>
    <entry><key>toplevels/top_panel/screen</key><schema_key>/schemas/apps/panel/toplevels/screen</schema_key></entry>
    <entry><key>toplevels/top_panel/monitor</key><schema_key>/schemas/apps/panel/toplevels/monitor</schema_key></entry>
    <entry><key>toplevels/top_panel/x</key><schema_key>/schemas/apps/panel/toplevels/x</schema_key></entry>
    <entry><key>toplevels/top_panel/y</key><schema_key>/schemas/apps/panel/toplevels/y</schema_key></entry>
    <entry><key>toplevels/top_panel/x_right</key><schema_key>/schemas/apps/panel/toplevels/x_right</schema_key></entry>
    <entry><key>toplevels/top_panel/y_bottom</key><schema_key>/schemas/apps/panel/toplevels/y_bottom</schema_key></entry>
    <entry><key>toplevels/top_panel/x_centered</key><schema_key>/schemas/apps/panel/toplevels/x_centered</schema_key></entry>
    <entry><key>toplevels/top_panel/y_centered</key><schema_key>/schemas/apps/panel/toplevels/y_centered</schema_key></entry>
    <entry><key>toplevels/top_panel/auto_hide</key><schema_key>/schemas/apps/panel/toplevels/auto_hide</schema_key></entry>
    <entry><key>toplevels/top_panel/enable_animations</key><schema_key>/schemas/apps/panel/toplevels/enable_animations</schema_key></entry>
    <entry><key>toplevels/top_panel/enable_buttons</key><schema_key>/schemas/apps/panel/toplevels/enable_buttons</schema_key></entry>
    <entry><key>toplevels/top_panel/enable_arrows</key><schema_key>/schemas/apps/panel/toplevels/enable_arrows</schema_key></entry>
    <entry><key>toplevels/top_panel/hide_delay</key><schema_key>/schemas/apps/panel/toplevels/hide_delay</schema_key></entry>
    <entry><key>toplevels/top_panel/unhide_delay</key><schema_key>/schemas/apps/panel/toplevels/unhide_delay</schema_key></entry>
    <entry><key>toplevels/top_panel/auto_hide_size</key><schema_key>/schemas/apps/panel/toplevels/auto_hide_size</schema_key></entry>
    <entry><key>toplevels/top_panel/background/type</key><schema_key>/schemas/apps/panel/toplevels/background/type</schema_key></entry>
    <entry><key>toplevels/top_panel/background/color</key><schema_key>/schemas/apps/panel/toplevels/background/color</schema_key></entry>
    <entry><key>toplevels/top_panel/background/opacity</key><schema_key>/schemas/apps/panel/toplevels/background/opacity</schema_key></entry>
    <entry><key>toplevels/top_panel/background/image</key><schema_key>/schemas/apps/panel/toplevels/background/image</schema_key></entry>
    <entry><key>toplevels/top_panel/background/fit</key><schema_key>/schemas/apps/panel/toplevels/background/fit</schema_key></entry>
    <entry><key>toplevels/top_panel/background/stretch</key><schema_key>/schemas/apps/panel/toplevels/background/stretch</schema_key></entry>
    <entry><key>toplevels/top_panel/background/rotate</key><schema_key>/schemas/apps/panel/toplevels/background/rotate</schema_key></entry>

  <!-- Bottom Panel -->

    <entry>
      <key>toplevels/bottom_panel/expand</key>
      <schema_key>/schemas/apps/panel/toplevels/expand</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/bottom_panel/disable_movement</key>
      <schema_key>/schemas/apps/panel/toplevels/disable_movement</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/bottom_panel/orientation</key>
      <schema_key>/schemas/apps/panel/toplevels/orientation</schema_key>
      <value>
        <string>bottom</string>
      </value>
    </entry>
    <entry>
      <key>toplevels/bottom_panel/size</key>
      <schema_key>/schemas/apps/panel/toplevels/size</schema_key>
      <value>
        <int>24</int>
      </value>
    </entry>
    <entry>
      <key>toplevels/bottom_panel/y_bottom</key>
      <schema_key>/schemas/apps/panel/toplevels/y_bottom</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>

    <entry><key>toplevels/bottom_panel/name</key><schema_key>/schemas/apps/panel/toplevels/name</schema_key></entry>
    <entry><key>toplevels/bottom_panel/screen</key><schema_key>/schemas/apps/panel/toplevels/screen</schema_key></entry>
    <entry><key>toplevels/bottom_panel/monitor</key><schema_key>/schemas/apps/panel/toplevels/monitor</schema_key></entry>
    <entry><key>toplevels/bottom_panel/x</key><schema_key>/schemas/apps/panel/toplevels/x</schema_key></entry>
    <entry><key>toplevels/bottom_panel/y</key><schema_key>/schemas/apps/panel/toplevels/y</schema_key></entry>
    <entry><key>toplevels/bottom_panel/x_right</key><schema_key>/schemas/apps/panel/toplevels/x_right</schema_key></entry>
    <entry><key>toplevels/bottom_panel/x_centered</key><schema_key>/schemas/apps/panel/toplevels/x_centered</schema_key></entry>
    <entry><key>toplevels/bottom_panel/y_centered</key><schema_key>/schemas/apps/panel/toplevels/y_centered</schema_key></entry>
    <entry><key>toplevels/bottom_panel/auto_hide</key><schema_key>/schemas/apps/panel/toplevels/auto_hide</schema_key></entry>
    <entry><key>toplevels/bottom_panel/enable_animations</key><schema_key>/schemas/apps/panel/toplevels/enable_animations</schema_key></entry>
    <entry><key>toplevels/bottom_panel/enable_buttons</key><schema_key>/schemas/apps/panel/toplevels/enable_buttons</schema_key></entry>
    <entry><key>toplevels/bottom_panel/enable_arrows</key><schema_key>/schemas/apps/panel/toplevels/enable_arrows</schema_key></entry>
    <entry><key>toplevels/bottom_panel/hide_delay</key><schema_key>/schemas/apps/panel/toplevels/hide_delay</schema_key></entry>
    <entry><key>toplevels/bottom_panel/unhide_delay</key><schema_key>/schemas/apps/panel/toplevels/unhide_delay</schema_key></entry>
    <entry><key>toplevels/bottom_panel/auto_hide_size</key><schema_key>/schemas/apps/panel/toplevels/auto_hide_size</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/type</key><schema_key>/schemas/apps/panel/toplevels/background/type</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/color</key><schema_key>/schemas/apps/panel/toplevels/background/color</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/opacity</key><schema_key>/schemas/apps/panel/toplevels/background/opacity</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/image</key><schema_key>/schemas/apps/panel/toplevels/background/image</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/fit</key><schema_key>/schemas/apps/panel/toplevels/background/fit</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/stretch</key><schema_key>/schemas/apps/panel/toplevels/background/stretch</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/rotate</key><schema_key>/schemas/apps/panel/toplevels/background/rotate</schema_key></entry>

  <!-- Menu Bar -->

    <entry>
      <key>objects/menu_bar/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>menu-bar</string>
      </value>
    </entry>
    <entry>
      <key>objects/menu_bar/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/menu_bar/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>
    <entry>
      <key>objects/menu_bar/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>objects/menu_bar/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>

    <entry><key>objects/menu_bar/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/menu_bar/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/menu_bar/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/menu_bar/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/menu_bar/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/menu_bar/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/menu_bar/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/menu_bar/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>objects/menu_bar/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Browser Launcher -->

    <entry>
      <key>objects/browser_launcher/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>launcher-object</string>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>1</int>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/launcher_location</key>
      <schema_key>/schemas/apps/panel/objects/launcher_location</schema_key>
      <value>
        <string>firefox.desktop</string>
      </value>
    </entry>

    <entry><key>objects/browser_launcher/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/browser_launcher/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/browser_launcher/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/browser_launcher/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/browser_launcher/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/browser_launcher/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/browser_launcher/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/browser_launcher/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Email Launcher -->

    <entry>
      <key>objects/email_launcher/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>launcher-object</string>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>2</int>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/locked</key>




      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/launcher_location</key>
      <schema_key>/schemas/apps/panel/objects/launcher_location</schema_key>
      <value>
        <string>evolution-mail.desktop</string>
      </value>
    </entry>

    <entry><key>objects/email_launcher/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/email_launcher/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/email_launcher/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/email_launcher/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/email_launcher/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/email_launcher/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/email_launcher/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/email_launcher/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

 <!-- Yelp Launcher -->

    <entry>
      <key>objects/yelp_launcher/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>launcher-object</string>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>4</int>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/launcher_location</key>
      <schema_key>/schemas/apps/panel/objects/launcher_location</schema_key>
      <value>
        <string>file:///usr/share/applications/yelp.desktop</string>
      </value>
    </entry>

    <entry><key>objects/yelp_launcher/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/yelp_launcher/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/yelp_launcher/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/yelp_launcher/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/yelp_launcher/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/yelp_launcher/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/yelp_launcher/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/yelp_launcher/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

 <!-- Mixer Applet -->

    <entry>
      <key>applets/mixer/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>3</int>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_MixerApplet</string>
      </value>
    </entry>

    <entry><key>applets/mixer/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/mixer/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/mixer/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/mixer/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/mixer/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/mixer/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/mixer/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/mixer/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Clock Applet -->

    <entry>
      <key>applets/clock/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/clock/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/clock/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>2</int>
      </value>
    </entry>
    <entry>
      <key>applets/clock/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/clock/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/clock/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_ClockApplet</string>
      </value>
    </entry>

    <entry><key>applets/clock/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/clock/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/clock/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/clock/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/clock/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/clock/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/clock/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/clock/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Clock Separator -->

    <entry>
      <key>objects/clock_separator/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>separator</string>
      </value>
    </entry>
    <entry>
      <key>objects/clock_separator/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/clock_separator/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>1</int>
      </value>
    </entry>
    <entry>
      <key>objects/clock_separator/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>objects/clock_separator/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>

    <entry><key>objects/clock_separator/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/clock_separator/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/clock_separator/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/clock_separator/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/clock_separator/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/clock_separator/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/clock_separator/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/clock_separator/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>objects/clock_separator/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Notification Area Applet -->

    <entry>
      <key>applets/notification_area/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>4</int>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_NotificationAreaApplet</string>
      </value>
    </entry>

    <entry><key>applets/notification_area/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/notification_area/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/notification_area/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/notification_area/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/notification_area/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/notification_area/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/notification_area/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/notification_area/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Fast User Switch Applet -->

    <entry>
      <key>applets/fast_user_switch/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_FastUserSwitchApplet</string>
      </value>
    </entry>

    <entry><key>applets/fast_user_switch/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/fast_user_switch/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/fast_user_switch/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/fast_user_switch/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/fast_user_switch/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/fast_user_switch/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/fast_user_switch/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/fast_user_switch/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Show Desktop Applet -->

    <entry>
      <key>applets/show_desktop_button/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>bottom_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_ShowDesktopApplet</string>
      </value>
    </entry>

    <entry><key>applets/show_desktop_button/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/show_desktop_button/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/show_desktop_button/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/show_desktop_button/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/show_desktop_button/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/show_desktop_button/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/show_desktop_button/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/show_desktop_button/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Window List Applet -->

    <entry>
      <key>applets/window_list/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>bottom_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>1</int>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_WindowListApplet</string>
      </value>
    </entry>

    <entry><key>applets/window_list/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/window_list/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/window_list/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/window_list/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/window_list/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/window_list/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/window_list/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/window_list/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Workspace Switcher Applet -->

    <entry>
      <key>applets/workspace_switcher/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>bottom_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>1</int>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_WorkspaceSwitcherApplet</string>
      </value>
    </entry>

    <entry><key>applets/workspace_switcher/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/workspace_switcher/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/workspace_switcher/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/workspace_switcher/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/workspace_switcher/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/workspace_switcher/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/workspace_switcher/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/workspace_switcher/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- TrashApplet Applet -->

    <entry>
      <key>applets/trashapplet/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>bottom_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_Panel_TrashApplet</string>
      </value>
    </entry>

    <entry><key>applets/trashapplet/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/trashapplet/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/trashapplet/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/trashapplet/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/trashapplet/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/trashapplet/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/trashapplet/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>

  </entrylist>

</gconfentryfile>
```

**3.** At the beginning where it says **<!-- List of toplevels -->** are the 2 panels that you have by default :

Top Panel :

```
<value>
            <string>top_panel</string>
          </value>

```

Bottom Panel :

```
<value>
            <string>bottom_panel</string>
          </value>

```

I removed the code of the bottom panel because i wanted the top panel only so mine looked like this :

```
<entry>
      <key>general/toplevel_id_list</key>
      <schema_key>/schemas/apps/panel/general/toplevel_id_list</schema_key>
      <value>
        <list type="string">
          <value>
            <string>top_panel</string>
          </value>
        </list>
      </value>
    </entry>

```

**4.** After that you have the list of the objects :

```
<!-- List of objects -->

```

and the list of applets :

```
<!-- List of applets -->

```

used in both (total) of the panels.

**5.** I removed :

```
<string>browser_launcher</string>
          </value>
          <value>
            <string>email_launcher</string>
          </value>
          <value>
            <string>yelp_launcher</string>

```

because i dont wanted the 3 icons of firefox , evolution and help near the menus in the top panel.

**6.** I changed in the Top Panel :

```
<!-- Top Panel -->

    <entry>
      <key>toplevels/top_panel/expand</key>
      <schema_key>/schemas/apps/panel/toplevels/expand</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/disable_movement</key>
      <schema_key>/schemas/apps/panel/toplevels/disable_movement</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/orientation</key>
      <schema_key>/schemas/apps/panel/toplevels/orientation</schema_key>
      <value>
        <string>top</string>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/size</key>
      <schema_key>/schemas/apps/panel/toplevels/size</schema_key>
      <value>
        <int>24</int>
      </value>
    </entry>

```

this value :

```
<value>
        <string>top</string>
      </value>
```

to this :

```
<value>
        <string>bottom</string>
      </value>
```

so the top panel goes to bottom and removed all this :

```
<!-- Bottom Panel -->

    <entry>
      <key>toplevels/bottom_panel/expand</key>
      <schema_key>/schemas/apps/panel/toplevels/expand</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/bottom_panel/disable_movement</key>
      <schema_key>/schemas/apps/panel/toplevels/disable_movement</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/bottom_panel/orientation</key>
      <schema_key>/schemas/apps/panel/toplevels/orientation</schema_key>
      <value>
        <string>bottom</string>
      </value>
    </entry>
    <entry>
      <key>toplevels/bottom_panel/size</key>
      <schema_key>/schemas/apps/panel/toplevels/size</schema_key>
      <value>
        <int>24</int>
      </value>
    </entry>
    <entry>
      <key>toplevels/bottom_panel/y_bottom</key>
      <schema_key>/schemas/apps/panel/toplevels/y_bottom</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>

    <entry><key>toplevels/bottom_panel/name</key><schema_key>/schemas/apps/panel/toplevels/name</schema_key></entry>
    <entry><key>toplevels/bottom_panel/screen</key><schema_key>/schemas/apps/panel/toplevels/screen</schema_key></entry>
    <entry><key>toplevels/bottom_panel/monitor</key><schema_key>/schemas/apps/panel/toplevels/monitor</schema_key></entry>
    <entry><key>toplevels/bottom_panel/x</key><schema_key>/schemas/apps/panel/toplevels/x</schema_key></entry>
    <entry><key>toplevels/bottom_panel/y</key><schema_key>/schemas/apps/panel/toplevels/y</schema_key></entry>
    <entry><key>toplevels/bottom_panel/x_right</key><schema_key>/schemas/apps/panel/toplevels/x_right</schema_key></entry>
    <entry><key>toplevels/bottom_panel/x_centered</key><schema_key>/schemas/apps/panel/toplevels/x_centered</schema_key></entry>
    <entry><key>toplevels/bottom_panel/y_centered</key><schema_key>/schemas/apps/panel/toplevels/y_centered</schema_key></entry>
    <entry><key>toplevels/bottom_panel/auto_hide</key><schema_key>/schemas/apps/panel/toplevels/auto_hide</schema_key></entry>
    <entry><key>toplevels/bottom_panel/enable_animations</key><schema_key>/schemas/apps/panel/toplevels/enable_animations</schema_key></entry>
    <entry><key>toplevels/bottom_panel/enable_buttons</key><schema_key>/schemas/apps/panel/toplevels/enable_buttons</schema_key></entry>
    <entry><key>toplevels/bottom_panel/enable_arrows</key><schema_key>/schemas/apps/panel/toplevels/enable_arrows</schema_key></entry>
    <entry><key>toplevels/bottom_panel/hide_delay</key><schema_key>/schemas/apps/panel/toplevels/hide_delay</schema_key></entry>
    <entry><key>toplevels/bottom_panel/unhide_delay</key><schema_key>/schemas/apps/panel/toplevels/unhide_delay</schema_key></entry>
    <entry><key>toplevels/bottom_panel/auto_hide_size</key><schema_key>/schemas/apps/panel/toplevels/auto_hide_size</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/type</key><schema_key>/schemas/apps/panel/toplevels/background/type</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/color</key><schema_key>/schemas/apps/panel/toplevels/background/color</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/opacity</key><schema_key>/schemas/apps/panel/toplevels/background/opacity</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/image</key><schema_key>/schemas/apps/panel/toplevels/background/image</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/fit</key><schema_key>/schemas/apps/panel/toplevels/background/fit</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/stretch</key><schema_key>/schemas/apps/panel/toplevels/background/stretch</schema_key></entry>
    <entry><key>toplevels/bottom_panel/background/rotate</key><schema_key>/schemas/apps/panel/toplevels/background/rotate</schema_key></entry>

```

that is the bottom panel.

I removed also the Firefox , Evolution and Help parts :

```
<!-- Browser Launcher -->

    <entry>
      <key>objects/browser_launcher/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>launcher-object</string>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>1</int>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>objects/browser_launcher/launcher_location</key>
      <schema_key>/schemas/apps/panel/objects/launcher_location</schema_key>
      <value>
        <string>firefox.desktop</string>
      </value>
    </entry>

    <entry><key>objects/browser_launcher/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/browser_launcher/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/browser_launcher/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/browser_launcher/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/browser_launcher/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/browser_launcher/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/browser_launcher/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/browser_launcher/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Email Launcher -->

    <entry>
      <key>objects/email_launcher/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>launcher-object</string>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>2</int>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>objects/email_launcher/launcher_location</key>
      <schema_key>/schemas/apps/panel/objects/launcher_location</schema_key>
      <value>
        <string>evolution-mail.desktop</string>
      </value>
    </entry>

    <entry><key>objects/email_launcher/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/email_launcher/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/email_launcher/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/email_launcher/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/email_launcher/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/email_launcher/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/email_launcher/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/email_launcher/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

 <!-- Yelp Launcher -->

    <entry>
      <key>objects/yelp_launcher/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>launcher-object</string>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>4</int>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>objects/yelp_launcher/launcher_location</key>
      <schema_key>/schemas/apps/panel/objects/launcher_location</schema_key>
      <value>
        <string>file:///usr/share/applications/yelp.desktop</string>
      </value>
    </entry>

    <entry><key>objects/yelp_launcher/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/yelp_launcher/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/yelp_launcher/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/yelp_launcher/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/yelp_launcher/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/yelp_launcher/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/yelp_launcher/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/yelp_launcher/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

```

**7.** Scroll down and find the Show Desktop Applet :

```
<!-- Show Desktop Applet -->

    <entry>
      <key>applets/show_desktop_button/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>bottom_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_ShowDesktopApplet</string>
      </value>
    </entry>

```

I changed the value:

```
<value>
        <string>bottom_panel</string>
      </value>

```

to

```
<value>
        <string>top_panel</string>
      </value>

```

so it goes to the top panel and to stick it near the menus i changed :

```
<schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>0</int>
      </value>
```

to :

```
<schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>1</int>
      </value>
```

This is the position of the icon. You have to set it to 1 because the sorting order of the applets and objects in the panel start from **left to right** and **from 0 to 1,2,3,4,5 and so on**. 

So if the value :

```
<schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
```

is **false** this means the objects and applets inside the panel will start to sort from left to right.

If you set that value to **true** you can use always the numbers but the icons will be sorted from the right part of the panel.


I made changes also in **<!-- Window List Applet -->** , **<!-- Workspace Switcher Applet -->** and **<!-- TrashApplet Applet -->** so they are positioned in the top panel.


**8.** **[COLOR="Red"]Do all the changes you like in the remaining parts of the file and save the file. At the bottom of this post i will paste also my new file so you can create an idea.[/COLOR]**

**9.**VERY IMPORTANT. PAY CLOSE ATTENTION TO THIS 3 COMMANDS BECAUSE WITHOUT DOING EXACTLY THIS COMMANDS IT WONT WORK. 

Now using gconftool-2 i updated the default xml file to make possible the changes (always in chroot) :

```
gconftool-2 --direct \
```
```
--config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
```
```
--load /etc/gconf/schemas/panel-default-setup.entries
```

Doing the first command you will have an arrow like this **>**. When you will do the third command you will be returned to chroot.

Compile your Live CD and you will have the new panel.

As i said at the beginning of this post, you can check : [**[COLOR="Black"]LiveCDCustomization[/COLOR]**]("https://help.ubuntu.com/community/LiveCDCustomization") for more info on editing and compiling the LiveCD

[COLOR="Black"][B]======================
Screenshot
======================[/B][/COLOR]

[IMG]http://s5.tinypic.com/2yngdux.jpg[/IMG]

[COLOR="Black"][B]======================
My file to make the panel like in the screenshot
======================[/B][/COLOR]

```
<gconfentryfile>

  <entrylist base="/apps/panel/default_setup">

    <!-- List of toplevels -->

    <entry>
      <key>general/toplevel_id_list</key>
      <schema_key>/schemas/apps/panel/general/toplevel_id_list</schema_key>
      <value>
        <list type="string">
          <value>
            <string>top_panel</string>
          </value>
        </list>
      </value>
    </entry>

    <!-- List of objects -->

    <entry>
      <key>general/object_id_list</key>
      <schema_key>/schemas/apps/panel/general/object_id_list</schema_key>
      <value>
        <list type="string">
          <value>
            <string>menu_bar</string>
          </value>
          <value>
            <string>clock_separator</string>
          </value>
        </list>
      </value>
    </entry>

    <!-- List of applets -->

    <entry>
      <key>general/applet_id_list</key>
      <schema_key>/schemas/apps/panel/general/applet_id_list</schema_key>
      <value>
        <list type="string">
          <value>
            <string>mixer</string>
          </value>
          <value>
            <string>clock</string>
          </value>
          <value>
            <string>notification_area</string>
          </value>
          <value>
            <string>show_desktop_button</string>
          </value>
          <value>
            <string>window_list</string>
          </value>
          <value>
            <string>workspace_switcher</string>
          </value>
          <value>
            <string>trashapplet</string>
          </value>
          <value>
            <string>fast_user_switch</string>
          </value>
        </list>
      </value>
    </entry>

  <!-- Top Panel -->

    <entry>
      <key>toplevels/top_panel/expand</key>
      <schema_key>/schemas/apps/panel/toplevels/expand</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/disable_movement</key>
      <schema_key>/schemas/apps/panel/toplevels/disable_movement</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/orientation</key>
      <schema_key>/schemas/apps/panel/toplevels/orientation</schema_key>
      <value>
        <string>bottom</string>
      </value>
    </entry>
    <entry>
      <key>toplevels/top_panel/size</key>
      <schema_key>/schemas/apps/panel/toplevels/size</schema_key>
      <value>
        <int>24</int>
      </value>
    </entry>

    <entry><key>toplevels/top_panel/name</key><schema_key>/schemas/apps/panel/toplevels/name</schema_key></entry>
    <entry><key>toplevels/top_panel/screen</key><schema_key>/schemas/apps/panel/toplevels/screen</schema_key></entry>
    <entry><key>toplevels/top_panel/monitor</key><schema_key>/schemas/apps/panel/toplevels/monitor</schema_key></entry>
    <entry><key>toplevels/top_panel/x</key><schema_key>/schemas/apps/panel/toplevels/x</schema_key></entry>
    <entry><key>toplevels/top_panel/y</key><schema_key>/schemas/apps/panel/toplevels/y</schema_key></entry>
    <entry><key>toplevels/top_panel/x_right</key><schema_key>/schemas/apps/panel/toplevels/x_right</schema_key></entry>
    <entry><key>toplevels/top_panel/y_bottom</key><schema_key>/schemas/apps/panel/toplevels/y_bottom</schema_key></entry>
    <entry><key>toplevels/top_panel/x_centered</key><schema_key>/schemas/apps/panel/toplevels/x_centered</schema_key></entry>
    <entry><key>toplevels/top_panel/y_centered</key><schema_key>/schemas/apps/panel/toplevels/y_centered</schema_key></entry>
    <entry><key>toplevels/top_panel/auto_hide</key><schema_key>/schemas/apps/panel/toplevels/auto_hide</schema_key></entry>
    <entry><key>toplevels/top_panel/enable_animations</key><schema_key>/schemas/apps/panel/toplevels/enable_animations</schema_key></entry>
    <entry><key>toplevels/top_panel/enable_buttons</key><schema_key>/schemas/apps/panel/toplevels/enable_buttons</schema_key></entry>
    <entry><key>toplevels/top_panel/enable_arrows</key><schema_key>/schemas/apps/panel/toplevels/enable_arrows</schema_key></entry>
    <entry><key>toplevels/top_panel/hide_delay</key><schema_key>/schemas/apps/panel/toplevels/hide_delay</schema_key></entry>
    <entry><key>toplevels/top_panel/unhide_delay</key><schema_key>/schemas/apps/panel/toplevels/unhide_delay</schema_key></entry>
    <entry><key>toplevels/top_panel/auto_hide_size</key><schema_key>/schemas/apps/panel/toplevels/auto_hide_size</schema_key></entry>
    <entry><key>toplevels/top_panel/background/type</key><schema_key>/schemas/apps/panel/toplevels/background/type</schema_key></entry>
    <entry><key>toplevels/top_panel/background/color</key><schema_key>/schemas/apps/panel/toplevels/background/color</schema_key></entry>
    <entry><key>toplevels/top_panel/background/opacity</key><schema_key>/schemas/apps/panel/toplevels/background/opacity</schema_key></entry>
    <entry><key>toplevels/top_panel/background/image</key><schema_key>/schemas/apps/panel/toplevels/background/image</schema_key></entry>
    <entry><key>toplevels/top_panel/background/fit</key><schema_key>/schemas/apps/panel/toplevels/background/fit</schema_key></entry>
    <entry><key>toplevels/top_panel/background/stretch</key><schema_key>/schemas/apps/panel/toplevels/background/stretch</schema_key></entry>
    <entry><key>toplevels/top_panel/background/rotate</key><schema_key>/schemas/apps/panel/toplevels/background/rotate</schema_key></entry>

  <!-- Menu Bar -->

    <entry>
      <key>objects/menu_bar/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>menu-bar</string>
      </value>
    </entry>
    <entry>
      <key>objects/menu_bar/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/menu_bar/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>
    <entry>
      <key>objects/menu_bar/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>objects/menu_bar/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>

    <entry><key>objects/menu_bar/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/menu_bar/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/menu_bar/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/menu_bar/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/menu_bar/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/menu_bar/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/menu_bar/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/menu_bar/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>objects/menu_bar/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

 <!-- Mixer Applet -->

    <entry>
      <key>applets/mixer/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>3</int>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/mixer/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_MixerApplet</string>
      </value>
    </entry>

    <entry><key>applets/mixer/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/mixer/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/mixer/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/mixer/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/mixer/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/mixer/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/mixer/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/mixer/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Clock Applet -->

    <entry>
      <key>applets/clock/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/clock/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/clock/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>2</int>
      </value>
    </entry>
    <entry>
      <key>applets/clock/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/clock/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/clock/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_ClockApplet</string>
      </value>
    </entry>

    <entry><key>applets/clock/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/clock/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/clock/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/clock/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/clock/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/clock/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/clock/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/clock/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Clock Separator -->

    <entry>
      <key>objects/clock_separator/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>separator</string>
      </value>
    </entry>
    <entry>
      <key>objects/clock_separator/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>objects/clock_separator/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>1</int>
      </value>
    </entry>
    <entry>
      <key>objects/clock_separator/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>objects/clock_separator/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>

    <entry><key>objects/clock_separator/bonobo_iid</key><schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key></entry>
    <entry><key>objects/clock_separator/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>objects/clock_separator/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>objects/clock_separator/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>objects/clock_separator/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>objects/clock_separator/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>objects/clock_separator/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>objects/clock_separator/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>objects/clock_separator/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Notification Area Applet -->

    <entry>
      <key>applets/notification_area/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>4</int>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/notification_area/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_NotificationAreaApplet</string>
      </value>
    </entry>

    <entry><key>applets/notification_area/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/notification_area/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/notification_area/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/notification_area/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/notification_area/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/notification_area/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/notification_area/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/notification_area/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Fast User Switch Applet -->

    <entry>
      <key>applets/fast_user_switch/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/fast_user_switch/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_FastUserSwitchApplet</string>
      </value>
    </entry>

    <entry><key>applets/fast_user_switch/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/fast_user_switch/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/fast_user_switch/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/fast_user_switch/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/fast_user_switch/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/fast_user_switch/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/fast_user_switch/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/fast_user_switch/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Show Desktop Applet -->

    <entry>
      <key>applets/show_desktop_button/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>1</int>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/show_desktop_button/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_ShowDesktopApplet</string>
      </value>
    </entry>

    <entry><key>applets/show_desktop_button/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/show_desktop_button/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/show_desktop_button/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/show_desktop_button/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/show_desktop_button/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/show_desktop_button/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/show_desktop_button/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/show_desktop_button/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Window List Applet -->

    <entry>
      <key>applets/window_list/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>2</int>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>false</bool>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/window_list/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_WindowListApplet</string>
      </value>
    </entry>

    <entry><key>applets/window_list/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/window_list/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/window_list/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/window_list/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/window_list/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/window_list/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/window_list/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/window_list/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- Workspace Switcher Applet -->

    <entry>
      <key>applets/workspace_switcher/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>6</int>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/workspace_switcher/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_WorkspaceSwitcherApplet</string>
      </value>
    </entry>

    <entry><key>applets/workspace_switcher/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/workspace_switcher/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/workspace_switcher/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/workspace_switcher/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/workspace_switcher/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/workspace_switcher/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/workspace_switcher/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>
    <entry><key>applets/workspace_switcher/action_type</key><schema_key>/schemas/apps/panel/objects/action_type</schema_key></entry>

  <!-- TrashApplet Applet -->

    <entry>
      <key>applets/trashapplet/object_type</key>
      <schema_key>/schemas/apps/panel/objects/object_type</schema_key>
      <value>
        <string>bonobo-applet</string>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/toplevel_id</key>
      <schema_key>/schemas/apps/panel/objects/toplevel_id</schema_key>
      <value>
        <string>top_panel</string>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/position</key>
      <schema_key>/schemas/apps/panel/objects/position</schema_key>
      <value>
        <int>5</int>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/panel_right_stick</key>
      <schema_key>/schemas/apps/panel/objects/panel_right_stick</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/locked</key>
      <schema_key>/schemas/apps/panel/objects/locked</schema_key>
      <value>
        <bool>true</bool>
      </value>
    </entry>
    <entry>
      <key>applets/trashapplet/bonobo_iid</key>
      <schema_key>/schemas/apps/panel/objects/bonobo_iid</schema_key>
      <value>
        <string>OAFIID:GNOME_Panel_TrashApplet</string>
      </value>
    </entry>

    <entry><key>applets/trashapplet/attached_toplevel_id</key><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key> </entry>
    <entry><key>applets/trashapplet/tooltip</key><schema_key>/schemas/apps/panel/objects/tooltip</schema_key></entry>
    <entry><key>applets/trashapplet/use_custom_icon</key><schema_key>/schemas/apps/panel/objects/use_custom_icon</schema_key></entry>
    <entry><key>applets/trashapplet/custom_icon</key><schema_key>/schemas/apps/panel/objects/custom_icon</schema_key></entry>
    <entry><key>applets/trashapplet/use_menu_path</key><schema_key>/schemas/apps/panel/objects/use_menu_path</schema_key></entry>
    <entry><key>applets/trashapplet/menu_path</key><schema_key>/schemas/apps/panel/objects/menu_path</schema_key></entry>
    <entry><key>applets/trashapplet/launcher_location</key><schema_key>/schemas/apps/panel/objects/launcher_location</schema_key></entry>

  </entrylist>

</gconfentryfile>
```



**[COLOR="Red"]Thank You and I hope this helps someone.[/COLOR]**

---

### Post by zerothis on 2009-05-03
after "Compile your Live CD and you will have the new panel." in step 9, you might want to reiterate the link to 
<a href=https://help.ubuntu.com/community/LiveCDCustomization>LiveCDCustomization</a>

Other than that, looks great. I'll probably be using this myself in my attempts to win people over.

---

### Post by ermali86 on 2009-05-07
> **zerothis said:**
> after "Compile your Live CD and you will have the new panel." in step 9, you might want to reiterate the link to 
<a href=https://help.ubuntu.com/community/LiveCDCustomization>LiveCDCustomization</a>

Other than that, looks great. I'll probably be using this myself in my attempts to win people over.

thank you for your suggestion. i added it again at step 9. Its always better to remember it. :)

I am glad you like this

---


---
title: "Help with Gnome Extension coding"
date: 2017-09-06
forum: Desktop Environments
---

### Post by su:bhatta on 2017-09-06
Hi All,

I am not a programmer but toy with some.

I am trying to come up with a Shutdown button which will display in the Gnome Top Panel so that i don't have to go to the submenu and poweroff.
Like [this]("https://extensions.gnome.org/extension/944/logout-button-on-panel/") extension which displays a logout button in the panel.

I have used it to come up with a button being displayed in my panel for shutdown, but it does nothing.

Request help to  assign this button so that on clicking the button the shutdown prompt is given.

Here is the extension code I have so far got  :

```

const Gio = imports.gi.Gio;const Lang = imports.lang;
const Shell = imports.gi.Shell;
const St = imports.gi.St;
const Me = imports.misc.extensionUtils.getCurrentExtension();


const Main = imports.ui.main;
const GnomeSession = imports.misc.gnomeSession;
const LOGOUT_MODE_NORMAL = 0;
let _logoutButton = null;
let baseGIcon;
let hoverGIcon;
let buttonIcon;


function init() {


  _logoutButton = new St.Bin({ style_class: 'panel-button',
                reactive: true,
                can_focus: true,
                x_fill: true,
                y_fill: false,
                track_hover: true });
  baseGIcon = Gio.icon_new_for_string(Me.path + "/icons/poweroff.png");
  hoverGIcon = Gio.icon_new_for_string(Me.path + "/icons/poweroff.png");
  buttonIcon = new St.Icon({
    'gicon': Gio.icon_new_for_string(Me.path + "/icons/poweroff.png"),
    'style_class': 'system-status-icon'
  });


  _logoutButton.set_child(buttonIcon);
  _logoutButton.connect('button-press-event', _startGnomePrefs);
  _logoutButton.connect('enter-event', function() {
    _SetButtonIcon('hover');
  });
  _logoutButton.connect('leave-event', function(){
    _SetButtonIcon('base');
  });


}


function _startGnomePrefs () {
  global.log("logoutbutton:_startGnomePrefs");
}


function enable () {
  Main.panel._rightBox.insert_child_at_index(_logoutButton,0);
}


function disable () {
  Main.panel._rightBox.remove_actor(_logoutButton);
}


function _SetButtonIcon(mode) {
  if (mode === 'hover') {
    buttonIcon.set_gicon(hoverGIcon);
  } else {
    buttonIcon.set_gicon(baseGIcon);
  }
}
```

If I am not mistaken below lines are key, and I have got no clue what they should be :

```

const LOGOUT_MODE_NORMAL = 0;
let _logoutButton = null;

```

I have used [this]("https://extensions.gnome.org/extension/1056/gnome-shutdown-button/") gnome extension as reference. The problem with that extension is, it vanishes the battery icon from the tray as is correctly reported in reviews.
Hence my project to get a separate Poweroff button displayed in top panel.

Any help is appreciated.

Regards,

---

### Post by su:bhatta on 2017-09-27
This is taken care, hence marked Solved

---


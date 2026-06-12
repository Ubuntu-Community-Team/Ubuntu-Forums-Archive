---
title: "Extension question - finding &quot;hostname&quot;."
date: 2013-05-01
forum: Desktop Environments
---

### Post by dandaman96 on 2013-05-01
SOLVED... 
--------------------------------

After searching [https://extensions.gnome.org/](https://extensions.gnome.org/) and failing to come up with anything, I'm attempting to write a very simple extension to accomplish what should be a simple task.  

In the panel, the user menu currently displays the user name.  Because I have two machines on a KVM, both running the same version of gnome with the same background (a picture of my little daughter), I sometimes lose track of which machine I am on.  I would simply like to modify the user name shown in the top right of my screen to include the hostname of the machine I am on.  

I don't write extensions, I don't write javascript, but I would really like to figure out how to get this to work.  The code that I am working on is below, and the missing step is figuring out how to find the hostname of the machine and assign it to a variable (denoted by ??????????????????).  

Does anyone have any suggestions?  

```

const _hostName = ???????????????;
var userMenuName;
try {
    userMenuName = imports.ui.main.panel.statusArea['userMenu']
} catch(TypeError) {
    userMenuName = imports.ui.main.panel._statusArea['userMenu'];
}
_originalName = userMenuName._name.text;

function init() {
}

function enable() {
    userMenuName._name.text = _originalName + "@" + _hostName;
//    userMenuName._name.text = _originalName + "@tuxbox";
}

function disable() {
    userMenuName._name.text = _originalName;
}

```

---

### Post by Malac on 2013-05-01
Can't help with Code but there is an option to show full name or username in the Preferences just set one to full and the other to username. 

Hope this helps.

---

### Post by philhughes on 2013-05-02
The hostname is stored in /etc/hostname (and also hosts), so you "just" need to read the value in from that file. Can't help with the code though.

---

### Post by dandaman96 on 2013-05-03
> **philhughes said:**
> The hostname is stored in /etc/hostname (and also hosts), so you "just" need to read the value in from that file. Can't help with the code though.

Thanks for the tip.  That has been my problem though, finding a way to pull that info in.  I originally tried to use GLib, thinking $HOSTNAME was an environmental variable.  Turns out, it is not.  (Although $echo $HOSTNAME correctly displays my hostname, $env|grep 'host' gives no results.).  

If there was a way to execute $cat /etc/hostname in the javascript, I would be set.  But I've come up empty trying to find code to do so.  I'm obviously not searching the right terms, but that's where I'm stuck.

---

### Post by dandaman96 on 2013-05-03
Well, a little more time in Google finally paid off.  I knew it had to be a simple answer.  There was a solution using GLib.  See the code below.  

```
const GLib = imports.gi.GLib;

try {
    userMenuName = imports.ui.main.panel.statusArea['userMenu']
} catch(TypeError) {
    userMenuName = imports.ui.main.panel._statusArea['userMenu'];
}

_hostName = GLib.get_host_name();
_thisUserName = GLib.get_user_name();
_originalName = userMenuName._name.text;

function init() {
}

function enable() {
    userMenuName._name.text = _thisUserName + "@" + _hostName;
}

function disable() {
    userMenuName._name.text = _originalName;
}
```

---


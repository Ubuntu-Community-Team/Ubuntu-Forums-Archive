---
title: "Prevent workspace change when clicking app-launcher (Gnome3-Shell)"
date: 2012-06-03
forum: Desktop Environments
---

### Post by Bazon on 2012-06-03
Hello, 
when running a application on another then the momentary workspace, clicking on it's symbol in the app-launcher (left bar in activities view) changes the workspace and takes one to the running instance of that program.

I don't like that. 
I'd prefer to launch a new window of that program on the momentary workspace.

How can I set Gnome-Shell to behave like that?

---

### Post by Paddy Landau on 2012-06-03
That is very much how it should work; it takes you to your currently-open application, whether on the same workspace or another.

To open a new window, you can:

[LIST]
[*]Right-click the launcher icon and select *Open a New Window*; or
[/LIST]

[LIST]
[*]Click the icon with your mouse's middle-button; or
[/LIST]

[LIST]
[*]Hold Super; note the number that appears on your launcher icon; and press that number (e.g. Super-Shift-3).
[/LIST]

---

### Post by Bazon on 2012-06-03
I know middle-click and right-click, thanks, and I know some people like that behaviour, I don't. 

These unwanted workspace-changes really bother me. I want to stay on my current workspace until I explictly change it!

(PS: Hold super+number is unity, not Gnome-Shell...)

---

### Post by Paddy Landau on 2012-06-03
Sorry. That's how Ubuntu works.

Clicking the launcher icon = focus the application if already open

---

### Post by Bazon on 2012-06-03
When I started with Ubuntu, Ubuntu worked like: Control every detail as you like. Would be great, if it was like this still...

---

### Post by Bazon on 2012-06-03
(And by the way: as i started with Ubuntu, clicking on a launcher opened a new window on the current workspace. Each and every time... )

---

### Post by Bazon on 2012-06-03
Maybe it's possible to modificate the "DashClickFix" Gnome-Shell-Extension to behave like that?

Momentary, it launches a new instance with every click.
I would like to have a new instance only if there is no instance on the current workspace.

Momentary, the code of DashFixClick looks like that:

```
/**
 * Desc: this extension "fixes" the dash's default behavior when you 
 *       click on an icon. The defualt is to launch the app if none is 
 *       running and to switch to the current instance if it is already 
 *       running. This extension changes that to instead of switching to 
 *       it if it is already running it always launches a new instance.
 * 
 * Author: Gabriel Rossetti
 * Date: 2011-12-08
 * Version: 1.0
 */
const Main = imports.ui.main;
const AppDisplay = imports.ui.appDisplay;
const Shell = imports.gi.Shell;
const Clutter = imports.gi.Clutter;


var _original = null;

/**
 * The new version of the function, this always lanches a new version of 
 * the app regardless of if it is already running or not.
 * 
 * @param event the current event
 */
function _onActivate(event) {
  this.emit('launching');

  if (this._onActivateOverride) {
    this._onActivateOverride(event);
  } else {
    this.app.open_new_window(-1);
  }
  Main.overview.hide();
}

/**
 * Initialize the extension
 */
function init() {
  _original = AppDisplay.AppWellIcon.prototype._onActivate;
}

/**
 * Enable the extension
 */
function enable() {
  AppDisplay.AppWellIcon.prototype._onActivate = _onActivate;
}

/**
 * Disable the extension
 */
function disable() {
  
  AppDisplay.AppWellIcon.prototype._onActivate = _original;
}
```

Has anyone an odea how to modify it to my desired behaviour? :-)

---

### Post by Bazon on 2012-09-08
It took some time to get started, but now I have written a Gnome-Shell-Extension myself for that:

[https://extensions.gnome.org/extension/440/workspace-separation-on-dash/](https://extensions.gnome.org/extension/440/workspace-separation-on-dash/)

It's for Gnome-Shell 3.4, if you want to try it on another Version of Gnome-Shell, just send me a PM, I'm also interested in knowing on which Versions it works. :-)

---

### Post by markbl on 2012-09-08
> **Paddy Landau said:**
> 
To open a new window, you can:

[LIST]
[*]Right-click the launcher icon and select *Open a New Window*; or
[/LIST]

[LIST]
[*]Click the icon with your mouse's middle-button; or
[/LIST]

[LIST]
[*]Hold Super; note the number that appears on your launcher icon; and press that number (e.g. Super-Shift-3).
[/LIST]
Paddy, the above options are for Unity, not GNOME Shell which the OP is using. GNOME Shell uses CTRL+click to open a new instance in same workspace, and middle-click to open a new instance in same workspace.

Note OP this is better than the old approach to just open a new instance regardless. Unity, GNOME Shell, and latest Mac OSX Mission Control all work this way because it is better. All those professional UI designers know what they are doing.

OP, make sure you spend 5 mins familarising yourself with the [GNOME Shell Cheat Sheet](https://live.gnome.org/GnomeShell/CheatSheet). Everybody new to GNOME Shell should do this.

---

### Post by Bazon on 2012-09-08
ehm, markbl, please note that 
(a) this thread ist marked as "solved" now
(b) I wrote an extension for that now, you can be sure I don't need to read beginners guides anymore... ;-) 
(c) It's nice to decide for one selve what is most useful. And I like to stay on my workspace unless I explictly change it. (I use workspaces to seperate contexts, and for that it is common to have severall windows of one application on severall workspaces)

Thanks anyway! :-)

---

### Post by markbl on 2012-09-08
Well Bazon, in all the discussion here about this issue there was no mention of the standard way in gnome shell to do it, i.e. just a simple ctrl+leftclick.

---

### Post by Bazon on 2012-09-08
OK, concerning this, you are right. :-)

---

### Post by bjfar on 2012-12-09
> **markbl said:**
> Note OP this is better than the old approach to just open a new instance regardless. Unity, GNOME Shell, and latest Mac OSX Mission Control all work this way because it is better. All those professional UI designers know what they are doing.

I have been using Unity for over a year now, and I agree with the OP: the automatic window-switching annoys the crap out of me. I easily forget which workspace contains which application instances and end up having the workspace zoom all over the place constantly, which eats up loads of cpu I might add and so is not a fast graceful transition in a normal high-use situation. I'd much rather the Unity taskbar only tell me (and interact with) exactly what is on the current workspace.

---

### Post by markbl on 2012-12-09
> **bjfar said:**
> I have been using Unity for over a year now, and I agree with the OP ...

Are you sure you are in the right place? The OP was talking about Gnome Shell (as per the thread title) yet you are talking about Unity.

---


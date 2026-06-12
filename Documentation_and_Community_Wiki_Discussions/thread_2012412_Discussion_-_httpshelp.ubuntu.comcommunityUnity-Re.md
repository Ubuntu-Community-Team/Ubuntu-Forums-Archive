---
title: "Discussion - https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior](https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior)

Support threads should be posted in normal forums.

Thank you.

---

### Post by isaacj87 on 2012-07-02
Hello, all.

So, after a successful migration over to the wiki, I've been informed this is the place I can inform users of new updates to the Unity-revamped PPA!

Regarding the wiki: the alternative method, building Unity from source, has been updated to reflect the move from Github to Launchpad. It's easier for me to merge updates from upstream if the code lives on LP. Everything has been migrated over sucessfully and my Github repo is now obsolete.

Usually, I build packages soon after I make changes on LP, but if you guys would like to pull and build Unity, that option is still very much so available.

Regarding the PPA: I've received a few requests to include a way to disable the hidden menus. After exploring solutions that still align with "Unity's" way of handling menus, I've come up with a solution.

My inspiration drew from this bug report: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/789979]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/789979")

There is now an option in CCSM to allow menus to be permanently visible. The behavior works like the following:

- For unmaximized windows, the program name will always be cut-off. Window controls and title still remain within the window.
- For maximized windows, the title will not be visible; however, the window controls, alongside the menu, will always be visible.

Obviously, if the option is untoggled, the default behavior will return.

Packages are now available, with fixes from upstream, from the usual place. Here's the relevant changelog:

```
unity (5.12.0-0ubuntu3+ikarosdev3) precise; urgency=low

  * Cherry pick upstream fixes.
    - PluginAdapterCompiz: ignore offscreen windows when looking for top one. (LP: #996604)
    - Fix crash when a GError exception is triggered (LP: #778470)
    - Search bar can't be focused when invalid keys are pressed (LP: #931393)
    - Searching in the HUD freezes Unity (LP: #1016239)
    - The dash will now open when invoked while in spread/scale mode (LP: #944033)
    - Switcher focuses on its own window, instead of leaving it to the current one. Now Alt+F4 does not work while the switcher is active (LP: #926406)
    - Fix closing the shrunk HUD when clicking outside its geometry (LP: #962651)
    - Fix AP test, get_compiz_option wasn't included in utilities
    - IMTextEntry: don't ingore ctrl/alt keypress to make ibus still working
    - Hide the overlay when the spread is initiated (LP: #870284)
    - Fix dragging to the last position when out of the launcher (LP: #971421)
  * New Feature.
    - Add option to allow menus to be always visible (LP: #789979)
 -- Isaac Joseph <email address hidden>   Sun, 01 Jul 2012 12:30:23 -0500
```

I must give credits and thanks to Anton Frolov (anton0). I used code from his Unity branch to add an option to CCSM.

---

### Post by isaacj87 on 2012-07-22
Hello, all.

Since I haven't setup a blog or Twitter account, yet, I figured this is probably the best place to post updates.

Some new stuff is coming to the Unity Revamped PPA. With the release of Unity 5.14.0 stable, I have merged all fixes and changes into my branch on LP. Also, a user on WebUPD8 notified me that the "always visible menus" option did not work for dual-monitor setups. I believe I have located and fixed the problem for good. I have received a request to be able to enable/disable the expo icon on the launcher. I have gone ahead and implemented an option into CCSM.

Packages (5.14.0) will be coming soon. All of the stuff mentioned above is already available in my Unity branch on LP. If you'd like to go ahead and build Unity (I need some dual-monitor users to test the fix!), simply follow the instructions on the wiki page.

Happy Ubuntu-ing. :)

---

### Post by isaacj87 on 2012-07-29
Hello, all.

5.14.0 packages are currently being built for 32 and 64-bit systems. Here is the full changelog: 
```
unity (5.14.0-0ubuntu1+ikarosdev1) precise; urgency=low

   * New upstream release.
     - Unity launcher shows internal partitions after they have been unmounted
       (LP: #994163)
     - can't click to dismiss hud in the area where dynamic hud results are
       meant to appear (LP: #962651)
     - Spread/Scale should exit if Dash is invoked (LP: #944033)
     - Searching in the HUD freezes unity (LP: #1016239)
     - Dash - The search bar gets the focus when pressing invalid keys
       (LP: #931393)
     - unity crashed with NameError in reset_unity_compiz_profile(): global name
       'GError' is not defined (LP: #778470)
     - When number of workspaces is set to 1, the Spread no longer works
       (LP: #996604)
     - compiz crashed with SIGSEGV in CompWindow::id() from getPaintMask()
       from unity::UnityWindow::glPaint() (LP: #851982)
     - "Keyboard Shortcuts" overlay can cause annoyance (LP: #934062)
     - padding between last quicklist item and bottom edge is non-deterministic
       (changes randomly) (LP: #955158)
     - HUD Draws improperly while searching for results (LP: #932531)
     - compiz crashed with SIGSEGV in
       unity::ui::KeyboardUtil::GetKeycodeAboveKeySymbol() (LP: #920258)
     - Launcher - when a user starts dragging a item, any folded launcher icons
       that are valid drop receptacles should unfold (LP: #839717)
     - Dragging image from firefox/chrome to dock causes lagg/freeze
       (LP: #772445)
     - dash should open when pressing "super" in scale mode (LP: #1023811)
     - Multimonitor, Launcher - When the Launcher is set to autohide and
       'Sticky edges' are turned off, 'Launcher Edge Stop Overcome Pressure'
       seems to be broken when revealing the Launcher (LP: #987955)
     - Software Center add to launcher icon animation is delayed when the
       launcher is in auto-hide mode (LP: #1012896)
     - Purchased items are not being added to the Unity launcher (LP: #925014)
     - Unity Launcher Fails To Auto-Hide When Enabled & Installing Commercial
       Software (LP: #1002440)
     - Regression: shift+click on a launcher icon to open a new application
       instance gone (LP: #754565)
     - Regression: Installing apps causes a terrible visual glitch-- have to
       restart X.org. (LP: #981168)
     - Duplicated applications icons on quick application restart (LP: #1003574)
     - HUD - Formatting of text in the auto-complete is wrong (LP: #939436)
     - alt-backtick flickers between windows (LP: #987156)
     - [Hud] The result grid is not drawn in proximity of the search entry
       (LP: #1008603)
     - Dash and Launcher - As soon as a user starts dragging a file from the
       Dash, there is a 'flicker' before the Launcher icons that are valid drop
       receptacles re-saturate (LP: #863230)
     - [hud] The last button is not rounded (LP: #1008656)
     - Hud flickers when show up (LP: #1011507)
     - Dash maximise button changed location (LP: #987674)
     - launcher reordering "line" doesn't go to the bottom slot (LP: #971421)
     - Dash/HUD should close on "Spread" (LP: #870284)
     - Nothing should be written into the dash/hud searchbar when holding super,
       ctrl or Alt (LP: #1013751)
     - Dash - when a file is dragged from the Dash (Dash home, file lens, or
       music lens) and dropped on a Launcher icon, the Dash should automatically
       close (LP: #865168)
     - Fix crash caused by invalid barrier subscriptions (LP: #1020075)
  * Unity-revamped fixes.
    - Fix bug which causes "menu always visible" behavior to fail on multi-monitor setups
  * New features.
    - Add option to enable/disable expo icon on launcher
```

I have fixed the issue with the "menu always visible" option and multi-monitors and added an option to enable/disable the expo icon on the launcher. Have fun, guys!

EDIT: I should note that some of the items in the changelog may actually be old. I had released packages previously that may already contain the above fixes.

EDIT2: Sorry, all. I messed up something in the debian/docs file (prevented the build from completing). I had to put out a new version:

```
unity (5.14.0-0ubuntu1+ikarosdev2) precise; urgency=low

   * Fix debian/docs.
     - Remove call to a missing, unused README file that was blocking packages from building on LP.
```

---

### Post by isaacj87 on 2012-09-14
Hello, all.

The release of 5.16.0 came as a surprise to me as I'm full-time KDE user. I will merge the changes from 5.0 upstream and build packages.

There is, however, one problem. After the recent changes to Nux, the option to force the menus to be shown now has issues (graphical glitches are now present). A couple weeks ago, I tried to fix this, but was unsuccessful. I have neither the time nor know-how to fix the problem, but if someone comes up with a solution, I'd be happy to review and merge the changes.

So, unfortunately, the short-term solution is to remove the option. Hopefully, I can find some time in next few days to prep and build the 5.16.0 packages. For what it's worth, all the other options are still intact.

EDIT: I just noticed that the official 5.16.0 packages are still sitting in precise-proposed. If you don't have that repo enabled, you won't get the official packages until they move into precise-updates (i.e. you'll still be using my 5.14.0). Hopefully, I will get my 5.16.0 packages out before the official ones move into precise-updates.

---

### Post by Jack' on 2012-09-26
Unity 5.16 has been moved to precise-updates.

---

### Post by isaacj87 on 2012-09-26
> **Jack' said:**
> Unity 5.16 has been moved to precise-updates.

New packages have been sent up to be built. If it goes well, updates should come soon.

---

### Post by Jack' on 2012-09-27
> **isaacj87 said:**
> New packages have been sent up to be built. If it goes well, updates should come soon.

The update has arrived and it works nicely. Thanks :)

---

### Post by xelab on 2012-09-27
Hello,

when i'm doing "apt-get dist-upgrade", unity and ubuntu-desktop are removed and the system fails! I have to remove the ppa and reinstall unity.

(sorry if a don't speak good english, i'm french)

---

### Post by JRBASTIEN on 2012-09-30
I'm no developer but please someone help Isaac to put back the permanent global menu.  That was the best feature you could add to Ubuntu!

Thank you for this PPA.

---

### Post by x-shaney-x on 2012-10-01
Just wondering if there are plans to continue this effort in 12.10?
I worry that as unity progresses it will be harder to keep bringing dodge back?

---

### Post by tekstr1der on 2012-12-06
@isaacj87: Unity 5.18 has been moved to precise-updates. I hope you'll still be building the patched version in your ppa.

The minimize-on-click behavior is hard to be without, even for a few hours!

Thanks for your work.

---


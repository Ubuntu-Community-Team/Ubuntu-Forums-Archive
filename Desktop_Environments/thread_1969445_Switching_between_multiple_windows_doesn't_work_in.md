---
title: "Switching between multiple windows doesn't work in Ubuntu 12.04"
date: 2012-04-30
forum: Desktop Environments
---

### Post by HPA on 2012-04-30
When a running application has multiple windows open, there are multiple white arrows on the left side of the application icon in the launcher.
If you click the application icon a second time, then all open windows are shown zoomed out. 
Then you can click the window you want to switch to it.
After an upgrade to Ubuntu 12.04 LTS, this feature was disabled  in both of my laptops.
My laptops' features are the following:
1. Sony Vaio VGN-NR31Z/S: Intel Core 2 Duo T5550 (1.83 GHz) / 3 GB RAM /  NVIDIA GeForce 8400 MGT GPU |O/S: Ubuntu 12.04 LTS 32bit
2.  HP Probook 4520s: Intel Core i3-370M (2.40 GHz) / 3 GB RAM / ATI  Mobility Radeon HD 4500 | O/S: Ubuntu 12.04 LTS 64bit

How can I fix this problem and restore the feature of switching windows of the same application by clicking their application icon on the launcher?
Thank you in advance.

---

### Post by anejo on 2012-04-30
I'm on 12.04... *(on two laptops as well)*
If I have more than one arrow, say three and select that icon, I get three windows that display and I pick the one I want to use! Is that what you're talking about?

---

### Post by HPA on 2012-04-30
> **anejo said:**
> I'm on 12.04... *(on two laptops as well)*
If I have more than one arrow, say three and select that icon, I get three windows that display and I pick the one I want to use! Is that what you're talking about?Yes.
I'm talking about this.
This feature has been disabled after my upgrade to Ubuntu 12.04.
Is there any solution for this?

---

### Post by anejo on 2012-04-30
Bummer... 'cos it does work so shouldn't it on your setups...?
Ok. Umm... and resetting Unity with a... 'unity --replace' ?
Does that change anything?

---

### Post by stinkeye on 2012-04-30
This function is controlled by the Scale and Scale Addons plugins in CCSM.
The Scale Addons plugin allows the zoom toggle and close with middle mouse.

---

### Post by piwacet on 2012-05-01
What has changed is that instances of the application that are on the current workspace will be shown in a zoomed out way as before, but if the instances of the application are on different workspaces, they will no longer be shown in the scale-plugin "zoomed out" view with 12.04.  This was an intentional design decision:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733)

Personally I also am quite adjusted to the old behavior, and need to research if there is a way to get the old behavior back.

---

### Post by stinkeye on 2012-05-01
Yep, they changed that which I also miss.

---

### Post by HPA on 2012-05-01
Thanks for your help.
In previous versions of Ubuntu I had removed the workspace switcher button from the launcher (because I didn't needit and it also occupied space there), by reducing the number of workspaces to 1 (1 vertical x 1 horizontal) with gconf (ccsm does the same thing as well).
This action didn't influence the switching between windows of the same application (e.g. of Mozilla Firerfox).
Unfortunately, now, in Ubuntu 12.04 the only way to enable switching between windows of the same application is to enable multiple workspaces.
_I did it very recently and this solved the problem of switching between windows of the same app_, but the problem is that the workspace switcher button reappeared in the launcher.
I  always work in one workspace and the workspace switcher button is annoying since it occupies space in the launcher.
Is there any solution in Ubuntu 12.04 to get rid of the workspace switcher button without affecting the switching of windows of the same application?
Thanks again.

---

### Post by stinkeye on 2012-05-01
If your only using the one workspace, why doesn't switching between windows of the same application work, as they must be on the same workspace?
How did you remove the workspace switcher?

[COLOR="Red"]Edit:[/COLOR] I just enabled 1 workspace,logged out/in
and the workspace switcher disappeared.
Switching between windows of the same application still works.

---

### Post by HPA on 2012-05-01
> **stinkeye said:**
> If your only using the one workspace, why doesn't switching between windows of the same application work, as they must be on the same workspace?
How did you remove the workspace switcher?In previous Ubuntu versions, I followed this:
[http://ubuntuforums.org/showpost.php?p=10760186&postcount=10](http://ubuntuforums.org/showpost.php?p=10760186&postcount=10)
In Ubuntu 12.04 I think the "Preferences" dialog box of the old gnome panel looks a little bit changed so I can't follow exactly the same procedure.
I now decrease or increase the number of workspaces using gconf-editor:
apps/compiz-a/general/screen0/options.
There I choose the horizontal size (hsize) and the vertical size (vsize).
When I choose the value "1" for both sizes, then the switching between windows of the same application is disabled.
After restart the workspace switcher is removed.
You can do the same action with compiz (ccsm application): Go to "General Options" and the "Workspace size" tab to adjust the horizontal size, the vertical size and the total number of workspaces.
> **stinkeye said:**
> [COLOR=Red]Edit:[/COLOR] I just enabled 1 workspace,logged out/in
and the workspace switcher disappeared.
Switching between windows of the same application still works.How did you enable 1 workspace in Ubuntu 12.04?
Please describe the full procedure.
Thank you.

---

### Post by stinkeye on 2012-05-01
Ccsm...
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by HPA on 2012-05-01
> **stinkeye said:**
> [COLOR=Red]Edit:[/COLOR] I just enabled 1 workspace,logged out/in
and the workspace switcher disappeared.
Switching between windows of the same application still works.I enabled 1 workspace with the way you show in the screenshot (through cssm).
After restart the workspace switcher is gone but I still cannot switch between windows of the same application.
I am sure there is a bug.

---

### Post by stinkeye on 2012-05-01
> **HPA said:**
> I enabled 1 workspace with the way you show in the screenshot (through cssm).
After restart the workspace switcher is gone but I still cannot switch between windows of the same application.
I am sure there is a bug.

So your in the Ubuntu session with compiz as the window manager
```
echo $DESKTOP_SESSION
```
> glen@Precise:~$ echo $DESKTOP_SESSION
ubuntu

and you have enabled both the Scale and ScaleAddons plugins in ccsm.

Works here when tested with multiple nautilus windows.

---

### Post by HPA on 2012-05-01
> **stinkeye said:**
> So your in the Ubuntu session with compiz as the window manager
```
echo $DESKTOP_SESSION
```and you have enabled both the Scale and ScaleAddons plugins in ccsm.
Works here when tested with multiple nautilus windows.I had enabled Scale only.
Now I enabled ScaleAddon but the problem remains.
The windows of the same application don't switch.

---

### Post by mc4man on 2012-05-01
Try going into System Settings > User accounts & creating a new user & log into it.
Set it up for a single Ws, see if it works in that login

If so then something in your local config files is borked

---

### Post by HPA on 2012-05-02
Thanks for your help.
I created a new user and set only 1 workspace with ccsm.
Even before I logout, the switching between windows was disabled, and was still disabled after logout-login to the new user account.
Can we have any other suggestion?

---

### Post by ubiquitin.jf on 2012-05-02
I'm also having this problem and have tried every fix proposed in this thread.

---

### Post by billjoie on 2012-05-09
I have the same problem. I created a bug report, please check it out and confirm or add your comments.  [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/997084]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/997084")

---


---
title: "Env setting on Unity launcher seemingly ineffective"
date: 2013-10-18
forum: Desktop Environments
---

### Post by Zunino on 2013-10-18
Hello.

Upon running Eclipse Kepler on Ubuntu 13.10, I noticed a problem with the global menu. The main menu options are displayed on the top panel, but the respective pull-down submenus are not. After searching a little bit, I found out this is a known issue. There's even a workaround for it, which involved resetting the environment variable *UBUNTU_MENUPROXY* before launching the application (as shown in [http://ubuntuforums.org/showthread.php?t=2179107&p=12810053#post12810053](http://ubuntuforums.org/showthread.php?t=2179107&p=12810053#post12810053)).

So far so good. The problem is I've only managed to successfully use that workaround when launching the application from the command line. Doing so from the launcher panel does not work. Here are the contents of the *eclipse.desktop* file I wrote:
```
[Desktop Entry]
Type=Application
Name=Eclipse
Comment=Eclipse IDE (Kepler)
Icon=eclipse
Exec=env UBUNTU_MENUPROXY= eclipse
StartupNotify=true
Terminal=false
Categories=Development;IDE;Java;
```
Even though the execution line reads exactly the same as the one I use on the CLI, the global menu issue is present when the application is launched. I assume I'm missing something really basic here and would be glad to get some help on this issue.

Thank you in advance.

---

### Post by mc4man on 2013-10-18
What's weird about that report,  which is on the default repo eclipse,  is that here it doesn't use the global (app) menu at all, no need to specify an env
(eclipse-3.8.4-1

Anyway - 
where is the eclipse.desktop you created?

Also
If you were to create a small script, place in a bin dir. in your path & run from alt+F2 does it open with menus in eclipse
Ex. - 
a file named test1 placed in ~/bin or /usr/local/bin & made executable
```
#!/bin/sh
env UBUNTU_MENUPROXY= eclipse

```

Does running test1 produce in window menus?

---

### Post by Zunino on 2013-10-21
> **mc4man said:**
> What's weird about that report,  which is on the default repo eclipse,  is that here it doesn't use the global (app) menu at all, no need to specify an env
(eclipse-3.8.4-1)
I've actually downloaded Eclipse from the project website. I'll give it a try with the version from the repository and report back.
> **mc4man said:**
> Anyway - 
where is the eclipse.desktop you created?
In /usr/share/applications. I know I could have created it in my home directory, but I chose to make it "system-wide" and thought /usr/share/applications would be the right location in that case.
> **mc4man said:**
> Also
If you were to create a small script, place in a bin dir. in your path & run from alt+F2 does it open with menus in eclipse
Ex. - 
a file named test1 placed in ~/bin or /usr/local/bin & made executable
```
#!/bin/sh
env UBUNTU_MENUPROXY= eclipse

```
Does running test1 produce in window menus?
Yes, it does. However, even if I modify the Exec entry in eclipse.desktop to invoke this little script instead, the menus are still broken. It then occurred to me that it might be because I had created a link from /usr/bin/eclipse to /opt/eclipse-kepler/eclipse (where I have the IDE installed). I then deleted the link, making sure that "which eclipse" returned nothing. Next, I typed eclipse in the dash and launched the app, hoping that Unity would have to be using the Exec line in eclipse.desktop, but to no avail. Still broken menus. I'm not really sure what to try next (aside from installing Eclipse from the repos).

Anything else I should try?

Thanks.

---

### Post by Zunino on 2013-10-23
Just to bring closure to the topic, I'd like to report that I found the actual cause of the unwanted behavior. The thing is there was a different eclipse.desktop file in ~/.local/share/applications which would take precedence over the one in /usr/share/applications. I'm pretty sure I never created such file, at least not intentionally. But, anyway, deleting it got rid of the issue.

Regards.

---


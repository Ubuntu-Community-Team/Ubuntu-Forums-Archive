---
title: "&quot;Help&quot; for power management console &quot;General&quot; tab"
date: 2011-02-12
forum: Desktop Environments
---

### Post by carpetn on 2011-02-12
Running Ubuntu 10.04 and Gnome 2.30.2 on Lenovo 3000 N100.

When I go to the power management console/general tab, in the section "Action: When power button is pressed" I see only one option, "Ask me." 

I clicked the "help" button but when "help" opened, all it does is show a picture of the dialog box. There is no help offered there. The picture shows the option 'Hibernate' where my computer only shows "Ask me."

So:
1. Why doesn't "Help" help me on this?
2. Should I be able to change these options? How?

---

### Post by asmoore82 on 2011-02-12
I have an issue with that option dialog too.
I see all options for "power button," but not for "suspend button."
For "suspend button," I can only select "suspend" or "hibernate."
I want "Ask me" just like for the power button.

You can open ```
gconf-editor
``` and browse down to "/apps/gnome-power-manager/buttons/"
In there, you can set almost any action for every event.

It's a shame that the dialog doesn't simply present all of these options to the user.

---

### Post by carpetn on 2011-02-14
Thanks.

Strangely, when I logged on directly on the box rather than thru NoMaching remote desktop, the General tab showed all the options. Must be something with the limits imposed on remote access.

I need to use remote access because my laptop screen is on the fritz. But occasionaly (and arbitrarily, as nearly as I can tell--replacing the inverted did not help) it will pop on and function perfectly. Then, just as arbitrarily, it won't work. Just now it popped on for the first time in 3 or more weeks.

---


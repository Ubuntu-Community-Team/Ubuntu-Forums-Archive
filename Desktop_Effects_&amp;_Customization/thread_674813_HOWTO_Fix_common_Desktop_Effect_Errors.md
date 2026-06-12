---
title: "HOWTO: Fix common Desktop Effect Errors"
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by Angadude on 2008-01-22
Hello, I documented some of the troubles I faced whilst trying to enable the desktop effects.



1. "Desktop effects could not be enabled"

A. The reason this error is caused because your Ubuntu doesn't have the required packages/dependencies, or because your graphics card is playing the fool.



The most common reason, mainly noticed with ATi Cards, is caused due to incorrect drivers.

You may want to fix this with the following:

1. Google for: "Envy Drivers"

Envy is an automated driver fetching script.

2. Or enable Restricted Drivers, from System> Administration> Restricted Drivers, and enable the proprietary ATi Accelerator.



If this doesn't help, then relax. Your PC is probably lacking the essential dependencies.

Start your Synaptic Package Manager.


System>Administration>Synaptic Package Manager


Now we need to enable Repositories, which we'll do from:
Settings>Repositories.
Tick all of 'em, and hit Close.

Now Reload, by clicking the reload button.
Now search for the following and enable them:

1.xserver-xgl
2.compiz-settings-manager

Now, try enabling the Desktop Effects. :)


2. Extension error:
A.

This is only because you need those dependencies. Read solution one.


3. Stretched screen:
A. 
Most likely to be a resolution gimmick. If your not allowed or able to fix the resolution, I would be more than sure you are having the restricted driver running. Try disabling that.


Any other errors? I would but be glad to help.

---


---
title: "New to Ubuntu and Cedega, help please :)"
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by macuser26 on 2007-07-14
Hi, I'm a PPC user and trying to get cedega to work on my newly installed Ubuntu system. I have the libxx-dev libraries installed and was able to extract cedega using dpkg -i cedega.deb. However, when I type in cedega at my command prompt, it gives me a whole list of errors. I'm really at a loss as of what to do because I can't get it to even get to the setup point that every FAQ has. Should I ditch cedega and go with wine? Or is either of them even compatible with my PPC computer? Anyways, any help would be appreciated. Here is the error I keep getting when I type in cedega at my prompt.

Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2744, in <module>
    Point2Play_gui_ref = Point2Play_gui( Point2Play.Point2Play( config_file) )
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 453, in __init__
    self.setup_menu_and_toolbar()  # also checks to see if the wizard needs to be run
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 912, in setup_menu_and_toolbar
    self.run_wizard()
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 850, in run_wizard
    setup_wizard = setup_wizard_gui.SetupWizardDialog(self.Point2Play)
  File "/usr/lib/transgaming_cedega/setup_wizard_gui.py", line 52, in __init__
    self.detect_system_info()
  File "/usr/lib/transgaming_cedega/setup_wizard_gui.py", line 113, in detect_system_info
    system_info = system_detection.make_detected_system_info_dictionary()
  File "/usr/lib/transgaming_cedega/system_detection.py", line 378, in make_detected_system_info_dictionary
    "cpu_ghz": detect_cpu_ghz(),
  File "/usr/lib/transgaming_cedega/system_detection.py", line 74, in detect_cpu_ghz
    cpu_mhz = float(cpu_mhz[:-1])
ValueError: invalid literal for float(): 1000.000000MHz


Would love a point in the right direction. Thanks.

---

### Post by blithen on 2007-07-14
Well from my observation You need python plugins.
I would wait for someone more experienced to come along, but you should at least try to go to synaptic package manager, and install the python packages.

---

### Post by macuser26 on 2007-07-15
well, i installed all of the python things i could find in the package manager, i did search for python and installed like everything. it still gives me the same error when i type cedega at the prompt. also, what is my root password? it doesn't let me login as root when i type su root, it says authentication failure "Sorry". however when i type su amanda it works just fine.

---

### Post by Nkari on 2007-07-15
Shouldn't the password you need be the one you entered when you first setup? 

Unless you have changed it since.

---

### Post by macuser26 on 2007-07-15
that's the thing, i hvent changed it and it only lets me use that password on amanda, not root. i reformatted and it does the same thing

---


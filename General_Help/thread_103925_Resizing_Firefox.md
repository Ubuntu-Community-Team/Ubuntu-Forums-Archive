---
title: "Resizing Firefox"
date: 2005-12-15
forum: General Help
---

### Post by Bruce_C on 2005-12-15
Is there a way to set the 'Unmaximize Window' button to resize the window to a specific dimension and position?  Essentially, I'd like the window to occupy the left half of my desktop.

---

### Post by briancurtin on 2005-12-15
download the source, and hardcode the value of the dimensions of the left half of your screen.

---

### Post by twisted_steel on 2005-12-15
Another option is to look into [Devil's Pie]("http://www.burtonini.com/blog/computers/devilspie"). From the description, it looks like you can match windows to different rules - moving all Firefox windows to a certain position might be possible.

EDIT:
After installing it, you need to create a configuration file.  If you install using Synaptic, it creates a sample configuration file in /usr/share/doc/devilspie/examples/sample-config.xml.  At the bottom is an example on how to make all dictionary windows a certain size.  You should be able to modify this to match all Firefox windows.

---

### Post by Gurgeh on 2005-12-17
Christ, imagine hard coding a the window size into firefox's source. U must linux mad!

---


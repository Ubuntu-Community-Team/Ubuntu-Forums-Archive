---
title: "add/remove not loading"
date: 2009-02-04
forum: General Help
---

### Post by pietbez on 2009-02-04
hi, i am bran new here. my linux is 2 days old and i am exited about my change from dreaded vista. Woot woot!

ok, things have beeg going slow but im getting there, until a few hours ago when out of the blue, my add/remove aplication stopped working.

when i go to Aplications  /  add remove. i just get the small white spinning loader for about a minute, and then nothing.

i am so stuck.

---

### Post by geirha on 2009-02-04
Try starting it from the terminal to see if it gives any useful error messages there. 

Applications -> Accessories -> Terminal, then type in the terminal:
```
gnome-app-install
```

Paste the output here.

Also see if Synaptic is working.

System -> Administration -> Synaptic package manager

---

### Post by pietbez on 2009-02-04
OK, i get "Bus error" from the terminal

---

### Post by geirha on 2009-02-04
Could you paste the whole output? To copy and paste, mark the text with the left mouse button, then switch to the web browser and hit the middle mousebutton inside the textarea to paste it.

---

### Post by pietbez on 2009-02-04
```
piet@dorp:~$ gnome-app-install
Bus error
piet@dorp:~$ 


```

---

### Post by geirha on 2009-02-04
Oh, it really was just "Bus error", sorry. Anyway, I've never encountered that error myself, and the closest case I can find is this bug report: 

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567)

See if removing those .bin-files in /var/cache/apt/ has any effect on your problem.

---

### Post by mb_webguy on 2009-02-04
Try this command in the terminal: "sudo apt-get --reinstall install gnome-app-install"

If that doesn't help, try: "sudo update-apt-xapian-index"

---


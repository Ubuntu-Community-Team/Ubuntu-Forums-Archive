---
title: "System Monitor Panel - 2 cores?"
date: 2009-09-08
forum: Desktop Environments
---

### Post by davidcmc on 2009-09-08
I've added the "System Monitor" applet to the upper panel of Gnome.
Is there any way to make it read both cores separately and show a percentage instead of a graph?

Thanks.

---

### Post by steveneddy on 2009-09-08
It will only display the average of the two processor cores.

I don't understand why you need to see that info.

Click the monitor applet and the main system monitor application opens, just click the "Resources" tab and you can view both processor cores.

If you want something cool to look at install cpufire from the repos.

```
sudo apt-get install cpufire-applet
```

---

### Post by davidcmc on 2009-09-08
> **steveneddy said:**
> It will only display the average of the two processor cores.

I don't understand why you need to see that info.

Click the monitor applet and the main system monitor application opens, just click the "Resources" tab and you can view both processor cores.

If you want something cool to look at install cpufire from the repos.

```
sudo apt-get install cpufire-applet
```

Just found a cool one. It's called HardwareMonitor and is located in Synaptic.
You can configure a lot of things on it.
Also found another applet called NetSpeed (also located in Synaptic). It shows In/Out traffic monitor of your NIC.

---

### Post by steveneddy on 2009-09-12
> **davidcmc said:**
> Just found a cool one. It's called HardwareMonitor and is located in Synaptic.
You can configure a lot of things on it.
Alsos found another applet called NetSpeed (also located in Synaptic). It shows In/Out traffic monitor of your NIC.

The System Monitor applet that is already there in the Add to panel menu will show an average of both processors AND the network activity.

---

### Post by davidcmc on 2009-09-15
> **steveneddy said:**
> The System Monitor applet that is already there in the Add to panel menu will show an average of both processors AND the network activity.

Yeah, I've noticed that.
The problem is that the native "System Monitor" applet only shows in graphic mode. What I wanted was an applet that could show values as numbers or bars.

---


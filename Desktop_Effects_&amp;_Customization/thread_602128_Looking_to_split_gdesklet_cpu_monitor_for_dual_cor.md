---
title: "Looking to split gdesklet cpu monitor for dual core"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by henjenagin on 2007-11-03
Hi All,
Great distro, gutsy is I'm thinking. I've tried amd64 then went to Ubuntu Ultimate 1.6 as soon as it was ready. I think TheeMann is still working on the 64 bit version. Anyway, I moved from XP back in June and have been pleasantly frustrated, surprised, and now blown away with linux and the capabilities. I think I have a stack of at least 20 or so CD/DVDs of various distros and will stick with this one for a long time. I like the gdesklets, might even try kiba-dock or awn. But for now I'm trying to get the cpu monitor to show each of the dual cores in my system. I'm not I programmer but I think it's in this code somewhere. It may also have something to do with the x86 version? (why have 2 cpu version for 32 bit proc...?) Other dual cpu monitors I've seen have labeled the cpu's as cpu0 and cpu1. If I open two instances of this monitor (see attachment) should they not show the exact same load percentage and graph? They don't! They are never at the same load amount. The monitor setup refreshes every 500ms and they weren't started at the exact same time, so that should account for the differences, right? Or am I getting two separate processors information? Would somebody care to shed a little light? 

What if one of the lines in the source code grabbed the information from "value = "%s @ %s" %" something...[COLOR="Red"]cpu0[/COLOR]%something% and displayed that information and then modified the source code for the second one to say "value = "%s @ %s" %" something...[COLOR="red"]cpu1[/COLOR]%something%...

What if...??

```
def show_cpu_info(show):
        Dsp.lbl_cpu_info.visible = show
        Dsp.gauge_load.visible = Dsp.plot_load.visible = not show
        if (show):
            Dsp.lbl_cpu_info.value = "Bogomips: %.2f\n%s (%dkB cache)" % \
                              (sys.cpu_bogomips, sys.cpu_model, sys.cpu_cache)
    def get_load():
        load = int(sys.cpu_load)
        if (sys.cpu_clock > 1000.0):
            clock = sys.cpu_clock / 1000.0
            clock = str("%4.3f GHz" % clock)
        else:
            clock = str("%4.f MHz" % sys.cpu_clock)
        if (len(sys.cpu_model) > 15): cpu_model = sys.cpu_model[:14] + ".."
        else: cpu_model = sys.cpu_mode
        Dsp.lbl_cpu.value = "%s @ %s" % (cpu_model, clock)
        Dsp.cpu_load.value = "%d%%" % load
        Dsp.plot_load.value = Dsp.gauge_load.fill = load
        if (75 <= load): fade_to(255, 64, 0)
        else: fade_to(0, 0, 0)
        add_timer(refresh, get_load)
```

---

### Post by ButtonMasher on 2008-03-15
I would love to see an answer for this as I am currently using a Dual Athlon MP 2000+ system.  If gdesklets in not capable of displays two seperate CPUs (or cores), does anyone know of a widget system that does (adesklets, screenlets, etc)?

---


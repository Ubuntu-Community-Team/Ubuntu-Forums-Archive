---
title: "Building a simple USB counter"
date: 2008-10-01
forum: Education &amp; Science
---

### Post by lixy on 2008-10-01
Hi all,

I've been thinking of building a simple switch (3-pins, I suppose) that connects to the USB port and have something keep track of the number of presses. Now, I briefly skimmed USB specs and it's got four wires (Vdd+, Vdd-, Data+ and Data-) and I figured that letting the switch push a voltage across the data lines would do the job. But when trying to find a simple tutorial to get started, the simplest I could find involved PICs (I don't count the ones that hook an LED to the USB port).

The more I dig, the harder this seems. What could be built straight forward using a parallel port for example, turned out to be much trickier. I'll give up for now, but if I missed anything or you have some litterature you would recommend, please chime in.

Thanks for your time,

/lixy

---

### Post by chewearn on 2008-10-02
Yes, using to switch to cross the usb data pins would definitely not work.

The usb protocol defined by the usb specifications, can downloaded (free of charge) at [http://www.usb.org/developers](http://www.usb.org/developers).  However, I reckoned you wouldn't want to built a full usb controller from scratch.  :smile:

The easiest way, I think, would be to hack a usb device like a keyboard or mouse.

---

### Post by Proton Soup on 2008-10-02
a search for "usb digital i o" found this: [http://www.delcom-eng.com/products_USBIO.asp](http://www.delcom-eng.com/products_USBIO.asp)

yeah, i think you'd be better off with a USB device that has the same logic type and impedance matched inputs.  high speed digital lines are a lot different from old school TTL logic.

only other thing that comes to mind at the moment is that you may want to "debounce" your switch.  otherwise, you may drive yourself crazy trying to figure out why you get several counts for every one.

---

### Post by strombom on 2008-10-02
Get a usb-serial conversion cable, you could use one of the flow-control pins to read the state of a switch.

---


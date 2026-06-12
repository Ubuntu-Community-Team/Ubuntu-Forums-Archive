---
title: "How do I set a default audio output when using a KVM swtich?"
date: 2021-06-28
forum: Desktop Environments
---

### Post by abic on 2021-06-28
I use a KVM to switch between multiple computers and have 2 USB audio devices connected through the switch (one I use for media, the other I use for conference calls). My primary machine is using Ubuntu Desktop 20.04.2 LTS with the standard Gnome 3 Ubuntu desktop setup (using the out of the box pulse audio setup).

 Whenever I switch back to Ubuntu, it always defaults to using the conference calls device for output and I have to manually switch it back to the media DAC.

My question's this; Is there a setting (command line or otherwise) to set an ordered preference of default output when multiple are present? I'd rather not muck around with udev rules and odd ball scripts for this but will if I have to :/.

---

### Post by abic on 2021-06-28
For additional context, the USB DAC I use for listening to media is a Focusrite Scarlett 2i2 3rd gen (USB ID 1235:8210), and for conference calls I use a Jabra SPEAK 410 (USB ID 0b0e:0412) since it has decent noise cancellation built-in

---


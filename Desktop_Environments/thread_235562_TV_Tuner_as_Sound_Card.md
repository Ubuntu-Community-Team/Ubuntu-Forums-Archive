---
title: "TV Tuner as Sound Card"
date: 2006-08-13
forum: Desktop Environments
---

### Post by jasonlfunk on 2006-08-13
I have on board audio and an TV Tuner. If I want audio when I watch TV I have to either connect a cable from the audio out on my tuner to the audio in on my board or plug my speakers into the tv tuner. (Either way it is a hassle). I want to use my TV Tuner as my default sound card but it is not showing up under Sound Preferences. Is this possible? Thanks.

---

### Post by jasonlfunk on 2006-08-13
By the way:
0000:00:0a.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and A udio Decoder (rev 05)
        Subsystem: Micro-Star International Co., Ltd. MSI TV-@nywhere Master
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:00:0a.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio D ecoder [Audio Port] (rev 05)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 8606
        Flags: bus master, medium devsel, latency 32, IRQ 12
        Memory at df000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

---

### Post by foolsh on 2006-08-13
my tuner card has a audio out plug as well but also has an internal plug on the board if you have a cable and an extra input plug on your mother board (most do) then connecting it that way only makes you use the sound mixer to select the input source and volume.

---

### Post by Neobuntu on 2006-08-13
No. Your tuner card is not a sound card.

Use the suggestion above to patch over and into your soundcard. That is, you could wire it from tvcard to soundcard inside the box (unless you on a laptop and added tuner.)

It's possible for tuner to include a soundcard but it drives up the price. I know the USB VoIP phone ARE a sound card (but that complicates your setup too.) So you may not really want your TV tuner to have another built in soundcard.

Hope that helps.

---


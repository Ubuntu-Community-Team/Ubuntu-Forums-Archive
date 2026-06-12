---
title: "Pamming symbols and charachtors to key strokes"
date: 2023-10-26
forum: Desktop Environments
---

### Post by reut2 on 2023-10-26
I am teaching Math online, and I previously had several super- and subscripts and other Math symbols programmed into my keyboard.  I accomplished this using xmodmap.  I was able to use the windows key and the shift key, and I think also the combination of the two as modifiers so I could assign multiple                          characters to single keys using different modifier key combinations. 
I recently has to reinstall the latest version of Ubuntu (Ubuntu 22.04.3 LTS) because my hard drive crashed, and I lost lots of data...  Now I am having trouble accomplishing this.
Here is some code I have used and the output:

```
$ xmodmap -pm
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)


```

As a test I entered the following:
```
xmodmap -e "keycode 21 =  U2090 U2091 U2075 U2074 U2073"

```
I get &#8336;&#8337; which correspond to U2090 U2091 respectively using the unmodified key and the Shift key respectively.  I have tried many combinations of the shift, Control, Alt as modifiers, and I can only get the first to arguments.
When I originally worked on this a couple of years ago, and I don't remember exactly what I did and I lost the files with the xmodmap command codes I used.
**News flash**  I just wanted to do a bit of testing before I posted, and I remembered that I have a Hebrew Keyboard installed, and when I switched I got the characters for the 3rd and 4th Arguments using the Windows key--Yea!
My understanding is that I can get up to seven characters mapped to each key.  I have searched extensively and cannot seem to get this to work for me.
I am using the Xubuntu in case that makes a difference.
I just noticed that after switching to the other keyboard, the ALT key switched between keyboards which I do not think was the case prior to the reinstall on the OS.  

An help would be appreciated.

---

### Post by TheFu on 2023-10-27
xmodmap only works with X11, not Wayland. Might your install being using Wayland? If using X11 and xmodmap isn't working, I cannot help.  I don't think Xubuntu is using Wayland by default, but I don't actually know.The GPU it sees in the system could matter, since nvidia may be the trigger NOT to use Wayland, while AMD and Intel GPUs could. IDK.

Not elegant, but vi/**vim** are the same everywhere, so if you are willing to edit equations inside vim using the built-in _digraphs_, that could be a work-around for you, but probably not any non-Unix-nerd students.  [Https://vimhelp.org/digraph.txt.html](Https://vimhelp.org/digraph.txt.html)
Inside vim, :digraphs will get the full table.

---

### Post by vanadium on 2023-10-28
There does not seem to be good universal keyboard remapping tools for Linux Wayland. There is a [blog](https://foosel.net/til/how-to-remap-keys-under-linux-and-wayland/) here where a tool available on hitgub, [keyd](https://github.com/rvaiya/keyd) is used. Another tool that appears rather powerfull is [xremap](https://github.com/k0kubun/xremap). To use the feature where a key is only triggered when a certain application is active, you need a Gnome Shell extension [xremap](https://extensions.gnome.org/extension/5060/xremap/).

Did you consider using the Linux Compose key feature? It allows you to compose characters using a sequence of key strokes. You set up one key to act as the "Compose" key, for example <Right Ctrl>. Then, creating ¹ involves hitting <Right Ctrl><^><1>.

Another option is to try the (very recommendable) tool [espanso](https://espanso.org/). You can define text snippets with it, which are triggered by a shortcut. Thus, ";^1" could be set up as a trigger for entering ¹, etc (there are actually already user contributed configuration files for that.

Otherwise, there apparently

---

### Post by reut2 on 2023-10-29
I am not using Wayland as far as I know.

---

### Post by TheFu on 2023-10-29
> **reut2 said:**
> I am not using Wayland as far as I know.

You wouldn't necessarily know.  Canonical, in their finite wisdom, decided to start inflicting Wayland as the default since 20.04. Best to look up how to tell, run the command and to KNOW for sure, since many things are either Wayland compatible or Xorg/X11 compatible.  

I read a few days ago that Gnome is removing the X11 hooks from Gnome and someone put in a github "pull" request to do just that.  
[https://news.itsfoss.com/gnome-wayland-xorg/](https://news.itsfoss.com/gnome-wayland-xorg/)
[https://www.phoronix.com/news/GNOME-MR-Drop-X11-Session](https://www.phoronix.com/news/GNOME-MR-Drop-X11-Session)
[https://www.theregister.com/2023/10/13/gnome_proposes_dropping_x11/](https://www.theregister.com/2023/10/13/gnome_proposes_dropping_x11/)

They've said that Wayland was production ready since 2017 - I don't know which world they live in, but it still isn't production ready here.  Perhaps in another 10 yrs until it is production ready, if the current level of progress is any guide.  PulseAudio took about 15 yrs to become production ready.  I'm still waiting for systemd and systemd-resolved and netplan to get there.  Wayland doesn't have a good automation solution.  They've tried, but those tools seem to lack about 50% of the things I need.

---

### Post by vanadium on 2023-10-29
I see in the first post under "News flash** (was that there initially?) that Xubuntu is used, so definitely X11.

---

### Post by reut2 on 2023-10-29
You say to run the command to find out if I have Wayland or X11, but you didn't say what command.  Somebody suggested that I am running on X11 if I am running Xubuntu.

---

### Post by TheFu on 2023-10-30
> **reut2 said:**
> You say to run the command to find out if I have Wayland or X11, but you didn't say what command.  Somebody suggested that I am running on X11 if I am running Xubuntu.

There are many ways to find information. If you are going to be running Linux, you'll want to use all of them, not just asking here.  

I know there's 1 command to find the information, but I'd have to look it up just like you would, so I figured it would be good for you to do that yourself. A few years ago, when I needed to 100% know what I was using, I used DDG to find the answer of the command from a reputable source, then ran it. I can't remember if it was just looking for an environment variable or not.

I remember that Xubuntu only supported X11 a few years ago. I don't know if that is still the situation. Maybe it is, but maybe it isn't.  IDK.

---

### Post by vanadium on 2023-11-01
If you want help, perhaps edit your question. You prominently state you reinstalled the latest version of Ubuntu (Ubuntu 22.04.3 LTS), then somewhere on the end state you use Xubuntu  "in case that makes a difference". In addition, someone already gave a few suggestions, but you did not bother exploring any of them. If you actually prefer to stick with xmodmap to make this work, then make that clear from your question. Edit the title so it clearly reflects you want to achieve this that way. Otherwise, the tread will continue to lead nowhere and you will blame the forum for that.

---

### Post by reut2 on 2023-11-07
I am now using my laptop with an external keyboard attached.  I'm using X11. Xubuntu
Here is the code I entered which remaps the keypad numbers 0-9
```
[FONT=DejaVu Serif][SIZE=2]reuven@reuven-Latitude-E6440:~$ xmodmap -e "keycode 85=sixsuperior KP_6 U03B8 KP_6 U03B8 U03B8 U03B8" && xmodmap -e "keycode 79 = sevensuperior KP_7 sevensuperior KP_7 U2192 U2192 U2192" 
&&  xmodmap -e "keycode 80 = eightsuperior KP_8  eightsuperior KP_8 U0394 U0394 U0394" && xmodmap -e "keycode 81 = ninesuperior KP_9 ninesuperior KP_9  U03c0 U03c0 U03c0" 
&& xmodmap -e "keycode 87 = onesuperior KP_1 onesuperior KP_1  U2081 U2081 U2081" && xmodmap -e "keycode 88 = twosuperior KP_2 twosuperior KP_2  twosubscript twosubscript twosubscript" 
&& xmodmap -e "keycode 90 = zerosuperior KP_0 zerosuperior KP_0 zerosubscript zerosubscript zerosubscript" && xmodmap -e "keycode 85 = sixsuperior KP_6 U03B8 KP_6 sixsubscript sixsubscript sixsubscript" 
&& xmodmap -e "keycode 79 = sevensuperior KP_7 sevensuperior KP_7 sevensubscript sevensubscript sevensubscript" && xmodmap -e "keycode 80 = eightsuperior KP_8  eightsuperior KP_8 eightsubscript eightsubscript eightsubscript" 
&& xmodmap -e "keycode 81 = ninesuperior KP_9 ninesuperior KP_9  ninesubscript ninesubscript ninesubscript"  && xmodmap -e "keycode 89=threesuperior KP_3 threesuperior KP_3 threesubscript threesubscript threesubscript"  
&& xmodmap -e "keycode 83 = foursuperior KP_4  foursuperior KP_4 foursubscript foursubscript foursubscript"  && xmodmap -e "keycode 84 = fivesuperior KP_5 fivesuperior KP_5  fivesubscript fivesubscript fivesubscript"

reuven@reuven-Latitude-E6440:~$ 1234567890¹²³&#8308;&#8309;&#8310;&#8311;&#8312;&#8313;&#8304;&#8321;&#8322;&#8323;&#8324;&#8325;&#8326;&#8327;&#8328;&#8329;&#8320;[/SIZE][/FONT]

  
```
In the **terminal** when I type the unmodified I get standard numbers, superscript with shift, and subscript with Ctrl-Shift--that's great!
BUT I can only get the superscripts in any other program, the ctrl-shift combinations give me nothing.  I have tried many other key combinations including ALT Windows, cap lock, num lock

---


---
title: "Change Key Mappings for a Specific Device"
date: 2010-08-12
forum: Desktop Environments
---

### Post by eWheeler on 2010-08-12
Hello,

_The question_: Can I change keymaps for a specific device?   For example, can I change the keymap for a specific input device listed  in "xinput --list" ?

_Detail_
I have a laptop keyboard and a USB 10-key pad for which I have remapped keys.  Specifically, I have made the Keypad .0-9 work as numbers while numlock is off.  This is important because numlock overrides the behavior of many of the laptop keys (if you have a laptop, press numlock and you'll see what I mean).

Currently I use xmodmap to remap the 10-key and it works quite well (Num_Lock is now BackSpace):

```
cat <<EOT | while read expr; do xmodmap -e "$expr"; done

keycode 77 = BackSpace
keycode 90 = KP_0
keycode 91 = KP_Decimal

keycode 87 = KP_1
keycode 88 = KP_2
keycode 89 = KP_3

keycode 83 = KP_4
keycode 84 = KP_5
keycode 85 = KP_6

keycode 79 = KP_7
keycode 80 = KP_8
keycode 81 = KP_9
EOT
```So, is it possible to use xmodmap or some other tool to remap the keycodes or keysyms coming off a specific input device?  This is my xinput --list:

```
$ xinput --list
[...]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
  [...]
    &#8627; BTC USB Multimedia Keyboard                 id=11    [slave  keyboard (3)]
    &#8627; BTC USB Multimedia Keyboard                 id=12    [slave  keyboard (3)]
    &#8627; BTC USB Multimedia Keyboard                 id=14    [slave  keyboard (3)]
    &#8627; BTC USB Multimedia Keyboard                 id=15    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=17    [slave  keyboard (3)]
    &#8627; NOVATEK Kensington U+P Keyboard             id=20    [slave  keyboard (3)]
    &#8627; NOVATEK Kensington U+P Keyboard             id=21    [slave  keyboard (3)]
```-Eric

---


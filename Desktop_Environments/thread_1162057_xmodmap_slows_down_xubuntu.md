---
title: "xmodmap slows down xubuntu"
date: 2009-05-17
forum: Desktop Environments
---

### Post by arkusk on 2009-05-17
Hi all, 
sorry if this is the wrong category, I wasn't sure.

My problem is I am trying to change my keyboard layout in my Xubuntu 9.04 on a T42 ThinkPad (to Colemak with a couple of customisations).
What I do is this:

```
$ xmodmap /home/a/.Xmodmap

$ cat .Xmodmap
! xmodmap for the Colemak layout.
! 2006-01-01 Shai Coleman, http://colemak.com/ . Public domain. 

keycode  49 =        grave    asciitilde       dead_tilde        asciitilde            
keycode  10 =            1        exclam       exclamdown       onesuperior            
keycode  11 =            2     quotedbl        masculine       twosuperior            
keycode  12 =            3    numbersign      ordfeminine     threesuperior            
keycode  13 =            4        dollar             cent          sterling            
keycode  14 =            5       percent         EuroSign               yen            
keycode  15 =            6   asciicircum          hstroke           Hstroke            
keycode  16 =            7     ampersand              eth               ETH            
keycode  17 =            8      asterisk            thorn             THORN            
keycode  18 =            9     parenleft   leftsinglequotemark   leftdoublequotemark   
keycode  19 =            0    parenright  rightsinglequotemark   rightdoublequotemark  
keycode  20 =        minus    underscore           endash            emdash            
keycode  21 =        equal          plus         multiply          division            
                                                                          
keycode  24 =            q             Q       adiaeresis        Adiaeresis            
keycode  25 =            w             W            aring             Aring            
keycode  26 =            f             F           atilde            Atilde            
keycode  27 =            p             P           oslash          Ooblique            
keycode  28 =            g             G      dead_ogonek        asciitilde            
keycode  29 =            j             J          dstroke           Dstroke            
keycode  30 =            l             L          lstroke           Lstroke            
keycode  31 =            u             U           uacute            Uacute            
keycode  32 =            y             Y       udiaeresis        Udiaeresis            
keycode  33 =    semicolon         colon       odiaeresis        Odiaeresis            
keycode  34 =  bracketleft     braceleft    guillemotleft             U2039            
keycode  35 = bracketright    braceright   guillemotright             U203a            
keycode  51 =   numbersign         dead_tilde       asciitilde        asciitilde            
                                                                                     
keycode  38 =            a             A           aacute            Aacute            
keycode  39 =            r             R       dead_grave        asciitilde            
keycode  40 =            s             S           ssharp        asciitilde            
keycode  41 =            t             T       dead_acute  dead_doubleacute            
keycode  42 =            d             D   dead_diaeresis        asciitilde            
keycode  43 =            h             H       dead_caron        asciitilde            
keycode  44 =            n             N           ntilde            Ntilde            
keycode  45 =            e             E           eacute            Eacute            
keycode  46 =            i             I           iacute            Iacute            
keycode  47 =            o             O           oacute            Oacute            
keycode  48 =   apostrophe            at           otilde            Otilde            
                                                                                      
keycode  52 =            z             Z               ae                AE            
keycode  53 =            x             X  dead_circumflex        asciitilde            
keycode  54 =            c             C         ccedilla          Ccedilla            
keycode  55 =            v             V               oe                OE            
keycode  56 =            b             B       dead_breve        asciitilde            
keycode  57 =            k             K   dead_abovering        asciitilde            
keycode  58 =            m             M      dead_macron        asciitilde            
keycode  59 =        comma          less     dead_cedilla        asciitilde            
keycode  60 =       period       greater    dead_abovedot        asciitilde            
keycode  61 =        slash      question     questiondown        asciitilde            
                                                                                      
!keycode 66 =    BackSpace     BackSpace        BackSpace         BackSpace            
keycode  94 =    backslash           bar           endash            emdash            
keycode  65 =        space         space            space      nobreakspace            
keycode 108 =  Mode_switch   Mode_switch                                               
clear Lock


!clear Shift
clear Control
!clear Mod1
!clear Mod2
!clear Mod3
!clear Mod4
!clear Mod5

!add    Shift   = Shift_L Shift_R
add    Control = Control_L Control_R Caps_Lock
!add    Mod1    = Alt_L Alt_R
!add    Mod2    = Num_Lock
!add    Mod4    = Meta_L Meta_R
!add    Mod5    = Scroll_Lock 

!keycode   9 = Escape
!keycode  22 = BackSpace Terminate_Server
!keycode  23 = Tab ISO_Left_Tab
!keycode  36 = Return
!keycode  37 = Control_L
!keycode  50 = Shift_L
!keycode  62 = Shift_R
!keycode  63 = KP_Multiply XF86_ClearGrab
!keycode  64 = Alt_L Meta_L
!keycode  67 = F1 XF86_Switch_VT_1
!keycode  68 = F2 XF86_Switch_VT_2
!keycode  69 = F3 XF86_Switch_VT_3
!keycode  70 = F4 XF86_Switch_VT_4
!keycode  71 = F5 XF86_Switch_VT_5
!keycode  72 = F6 XF86_Switch_VT_6
!keycode  73 = F7 XF86_Switch_VT_7
!keycode  74 = F8 XF86_Switch_VT_8
!keycode  75 = F9 XF86_Switch_VT_9
!keycode  76 = F10 XF86_Switch_VT_10
!keycode  95 = F11 XF86_Switch_VT_11
!keycode  96 = F12 XF86_Switch_VT_12
!keycode  77 = Num_Lock Pointer_EnableKeys
!keycode  78 = Scroll_Lock
!keycode  79 = KP_Home KP_7
!keycode  80 = KP_Up KP_8
!keycode  81 = KP_Prior KP_9
!keycode  82 = KP_Subtract XF86_Prev_VMode
!keycode  83 = KP_Left KP_4
!keycode  84 = KP_Begin KP_5
!keycode  85 = KP_Right KP_6
!keycode  86 = KP_Add XF86_Next_VMode
!keycode  87 = KP_End KP_1
!keycode  88 = KP_Down KP_2
!keycode  89 = KP_Next KP_3
!keycode  90 = KP_Insert KP_0
!keycode  91 = KP_Delete KP_Decimal
!keycode  92 = Print Sys_Req
!keycode  93 = Mode_switch
!keycode  97 = Home
!keycode  98 = Up
!keycode  99 = Prior
!keycode 100 = Left
!keycode 102 = Right
!keycode 103 = End
!keycode 104 = Down
!keycode 105 = Next
!keycode 106 = Insert
!keycode 107 = Delete
!keycode 108 = KP_Enter
!keycode 109 = Control_R
!keycode 110 = Pause Break
!keycode 111 = Print Sys_Req
!keycode 112 = KP_Divide XF86_Ungrab
!keycode 114 = Pause Break
!keycode 115 = Super_L
!keycode 116 = Super_R
!keycode 117 = Menu
!keycode 124 = ISO_Level3_Shift
!keycode 125 = NoSymbol Alt_L
!keycode 126 = KP_Equal
!keycode 127 = NoSymbol Super_L
!keycode 128 = NoSymbol Hyper_L
!keycode 156 = NoSymbol Meta_L

!keycode   8 =
!keycode 101 =
!keycode 118 =
!keycode 119 =
!keycode 120 =
!keycode 121 =
!keycode 122 =
!keycode 123 =
!keycode 129 =
!keycode 130 =
!keycode 131 =
!keycode 132 =
!keycode 133 =
!keycode 134 =
!keycode 135 =
!keycode 136 =
!keycode 137 =
!keycode 138 =
!keycode 139 =
!keycode 140 =
!keycode 141 =
!keycode 142 =
!keycode 143 =
!keycode 144 =
!keycode 145 =
!keycode 146 =
!keycode 147 =
!keycode 148 =
!keycode 149 =
!keycode 150 =
!keycode 151 =
!keycode 152 =
!keycode 153 =
!keycode 154 =
!keycode 155 =
!keycode 157 =
!keycode 158 =
!keycode 159 =
!keycode 160 =
!keycode 161 =
!keycode 162 =
!keycode 163 =
!keycode 164 =
!keycode 165 =
!keycode 166 =
!keycode 167 =
!keycode 168 =
!keycode 169 =
!keycode 170 =
!keycode 171 =
!keycode 172 =
!keycode 173 =
!keycode 174 =
!keycode 175 =
!keycode 176 =
!keycode 177 =
!keycode 178 =
!keycode 179 =
!keycode 180 =
!keycode 181 =
!keycode 182 =
!keycode 183 =
!keycode 184 =
!keycode 185 =
!keycode 186 =
!keycode 187 =
!keycode 188 =
!keycode 189 =
!keycode 190 =
!keycode 191 =
!keycode 192 =
!keycode 193 =
!keycode 194 =
!keycode 195 =
!keycode 196 =
!keycode 197 =
!keycode 198 =
!keycode 199 =
!keycode 200 =
!keycode 201 =
!keycode 202 =
!keycode 203 =
!keycode 204 =
!keycode 205 =
!keycode 206 =
!keycode 207 =
!keycode 208 =
!keycode 209 =
!keycode 210 =
!keycode 211 =
!keycode 212 =
!keycode 213 =
!keycode 214 =
!keycode 215 =
!keycode 216 =
!keycode 217 =
!keycode 218 =
!keycode 219 =
!keycode 220 =
!keycode 221 =
!keycode 222 =
!keycode 223 =
!keycode 224 =
!keycode 225 =
!keycode 226 =
!keycode 227 =
!keycode 228 =
!keycode 229 =
!keycode 230 =
!keycode 231 =
!keycode 232 =
!keycode 233 =
!keycode 234 =
!keycode 235 =
!keycode 236 =
!keycode 237 =
!keycode 238 =
!keycode 239 =
!keycode 240 =
!keycode 241 =
!keycode 242 =
!keycode 243 =
!keycode 244 =
!keycode 245 =
!keycode 246 =
!keycode 247 =
!keycode 248 =
!keycode 249 =
!keycode 250 =
!keycode 251 =
!keycode 252 =
!keycode 253 =
!keycode 254 =
!keycode 255 = 

```Now the problems are as follows:

[LIST=1]
[*]my .Xmodmap does not seem to be loaded on startup
[*]when I add xmodmap /home/a/.Xmodmap to the autostarted apps, my keyboard layout is unmodified after startup, it is still QWERTZ. I've noticed before (with conky and other programs), autostart more often than not does not seem to work for me (I've tried using local.rc but to no avail).
[*]when I do xmodmap /home/a/.Xmodmap manually in the terminal, the layout switches, which is great. But often when I do this my machine becomes more and more unresponsive and sometimes even crashes totally (even ignores Sysrq then). htop says that the /usr/bin/X process consumes up to 90% of my 1.7 Ghz whenever this happens. I don't use Xubuntu's built-in keyboard layout switcher (which has a Colemak layout) because I don't know how to customise specific keys (and because the layout doesn't work for key combinations involving ctrl both in the terminal emulator and in java apps)
[/LIST]
I've spend literally days on all these issues and I don't know what else to try.

Any help appreciated.
Cheers
Arian

---

### Post by arkusk on 2009-05-17
Update:
Ok, so I installed avant window navigator today and when I tried to go to the keyboard settings tab via awn's main menu applet, I arrived in what looks like GNOMES keyboard setttings menu, not the standard Xubuntu one. Not sure where this came from as I haven't really customised my system much or installed lot's of GNOME packages. Anyway, I was finally able to set my keyboard layout the way I wanted. 

Still, if somebody could enlighten me as to what the proper way to achieve this in 'pure' XFCE would be, I'd be a happy chicken.

---

### Post by edvakf on 2009-05-25
The same thing happened to me too.

I installed xubuntu on top of my normal ubuntu by the command

```

sudo apt-get install xubuntu-desktop

```

Then I logged out once and opened a xfce session. My ~/.xmodmaprc wasn't recognized, and when I manually entered xmodmap ~/.xmodmaprc in the terminal, CPU started running like crazy. I had to Ctrl-C the process.

I gave up xubuntu and then opened a gnome session. My .xmodmap was still not applied. So I looked at the processes running at the time. "xfce4-settings-helper" looked suspicious to me, so I killed it. And now xmodmap works fine.

I suggest you search by "xfce4-settings-helper". Looks like there is some useful info.

[https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/97175](https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/97175)
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/363664](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/363664)

---

### Post by pointym5 on 2009-06-07
Neither of those bug reports address the bizarre CPU freakout that running *xmodmap* causes.  I haven't managed to strace it, but my experience is that simply launching *xmodmap* from a terminal in an XFCE session will completely lock up my machine for a period of well over a minute.  By "completely lock up" I mean just that - the machine is totally unresponsive - not slow, but absolutely frozen.

I've never seen that happen in any other desktop environment I've used over the past 20 years :-)

---

### Post by henriquemaia on 2009-12-17
I'm sorry for reviving an old thread, but I have the exact same problem. I can't get xmodmap to run my custom keymap without crashing the session (or making it unusable). Any ideas on how to overcome this?

ps: my keyboard has some key keys on weird places, so I really need my custom keymapping.

---

### Post by henriquemaia on 2009-12-18
Nothing like using and old method with updated paths. 

The xkb has its layouts stored in /usr/share/X11/xkb/symbols. You edit your preferred layout there (or create a new one), save it and restart your X session. Works like a charm. :)

---

### Post by balmar on 2010-07-20
Same problem here. I used to have Gnome, where this only happened if I did xmodmap while Openoffice was open, pretty funny. Now I changed to xfce and xmodmap always sends up the machine's load for a long time. I am living with this problem by minimizing my xmodmap file: it only has the 11 entries I want to change. This way it takes 7 seconds on my desktop and 35 seconds on an Eee pc.

Haven't tried the xkb method yet.

---

### Post by cheemosabe on 2011-02-23
I found a solution:

Go to ~/.config/xfce4/xfconf/xfce-perchannel-xml/keyboard-layout.xml and change

  <property name="XkbDisable" type="bool" value="false"/>

with

  <property name="XkbDisable" type="bool" value="true"/>

This disables selectable keyboard layouts in xfce. It also doesn't override any xmodmap settings that may have been set in xinitrc or anywhere before running xfce4-session.

---


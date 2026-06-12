---
title: "numpad not supported from firefox, gedit and &quot;sticky notes&quot;"
date: 2010-03-22
forum: Desktop Environments
---

### Post by phibuntu on 2010-03-22
Hi all

My strange probelm is, that firefox, gedit and "sticky notes" do not support the numpad (numeric pad; numblock, numeric block).

Digits work in most other applications (at least in all I use, like OpenOffice, Terminal, Eclipse, ...)

I am using gnome on ubuntu 9.10 and an external diNovo Logitec (but I have the same problem on the laptop keyboard, using "NumLk".
Here's my output from the ```
>xmodmap -pk
``` command:

```
There are 6 KeySyms per KeyCode; KeyCodes range from 8 to 255.

    KeyCode	Keysym (Keysym)	...
    Value  	Value   (Name) 	...

      8    	
      9    	0xff1b (Escape)	0x0000 (NoSymbol)	0xff1b (Escape)	0x0000 (NoSymbol)	0xff1b (Escape)	
     10    	0x0031 (1)	0x0021 (exclam)	0x00b9 (onesuperior)	
     11    	0x0032 (2)	0x0040 (at)	0x00b2 (twosuperior)	
     12    	0x0033 (3)	0x0023 (numbersign)	0x00b3 (threesuperior)	
     13    	0x0034 (4)	0x0024 (dollar)	
     14    	0x0035 (5)	0x0025 (percent)	
     15    	0x0036 (6)	0x005e (asciicircum)	
     16    	0x0037 (7)	0x0026 (ampersand)	
     17    	0x0038 (8)	0x002a (asterisk)	
     18    	0x0039 (9)	0x0028 (parenleft)	
     19    	0x0030 (0)	0x0029 (parenright)	
     20    	0x002d (minus)	0x005f (underscore)	0x00df (ssharp)	0x00df (ssharp)	
     21    	0x003d (equal)	0x002b (plus)	
     22    	0xff08 (BackSpace)	0xff08 (BackSpace)	0xfd1a (3270_DeleteWord)	
     23    	0xff09 (Tab)	
     24    	0x0071 (q)	0x0051 (Q)	
     25    	0x0077 (w)	0x0057 (W)	
     26    	0x006c (l)	0x004c (L)	
     27    	0x0076 (v)	0x0056 (V)	
     28    	0x006a (j)	0x004a (J)	
     29    	0x007a (z)	0x005a (Z)	
     30    	0x0075 (u)	0x0055 (U)	0x00fa (uacute)	0x00f9 (ugrave)	
     31    	0x006b (k)	0x004b (K)	
     32    	0x0068 (h)	0x0048 (H)	
     33    	0x0070 (p)	0x0050 (P)	
     34    	0x007b (braceleft)	0x007d (braceright)	0x00fc (udiaeresis)	0x00dc (Udiaeresis)	
     35    	0x005b (bracketleft)	0x005d (bracketright)	
     36    	0xff0d (Return)	0x0000 (NoSymbol)	0xff0d (Return)	0x0000 (NoSymbol)	0xff0d (Return)	
     37    	0xffe3 (Control_L)	
     38    	0x0074 (t)	0x0054 (T)	
     39    	0x0073 (s)	0x0053 (S)	
     40    	0x0072 (r)	0x0052 (R)	
     41    	0x006e (n)	0x004e (N)	0x00f1 (ntilde)	0x00d1 (Ntilde)	
     42    	0x0067 (g)	0x0047 (G)	
     43    	0x006f (o)	0x004f (O)	0x00f3 (oacute)	0x00f2 (ograve)	
     44    	0x0065 (e)	0x0045 (E)	0x00e9 (eacute)	0x00e8 (egrave)	
     45    	0x0069 (i)	0x0049 (I)	0x00ed (iacute)	0x00ec (igrave)	
     46    	0x0061 (a)	0x0041 (A)	0x00e1 (aacute)	0x00e0 (agrave)	
     47    	0x003b (semicolon)	0x003a (colon)	0x00f6 (odiaeresis)	0x00d6 (Odiaeresis)	
     48    	0x0027 (apostrophe)	0x0022 (quotedbl)	0x00e4 (adiaeresis)	0x00c4 (Adiaeresis)	
     49    	0x0060 (grave)	0x007e (asciitilde)	
     50    	0xffe1 (Shift_L)	0x0000 (NoSymbol)	0xffe1 (Shift_L)	0x0000 (NoSymbol)	0xffe1 (Shift_L)	
     51    	0x005c (backslash)	0x007c (bar)	
     52    	0x0079 (y)	0x0059 (Y)	
     53    	0x0062 (b)	0x0042 (B)	
     54    	0x0063 (c)	0x0043 (C)	0x00e7 (ccedilla)	0x00c7 (Ccedilla)	
     55    	0x0064 (d)	0x0044 (D)	
     56    	0x0078 (x)	0x0058 (X)	
     57    	0x0066 (f)	0x0046 (F)	
     58    	0x006d (m)	0x004d (M)	
     59    	0x002c (comma)	0x003c (less)	
     60    	0x002e (period)	0x003e (greater)	
     61    	0x002f (slash)	0x003f (question)	0x00bf (questiondown)	
     62    	0xffe2 (Shift_R)	0x0000 (NoSymbol)	0xffe2 (Shift_R)	0x0000 (NoSymbol)	0xffe2 (Shift_R)	
     63    	0xffaa (KP_Multiply)	0x10022c5 (U22C5)	0xffaa (KP_Multiply)	0x10022c5 (U22C5)	0x10000d7 (no name)	0x1008fe21 (XF86_ClearGrab)	
     64    	0xffe9 (Alt_L)	
     65    	0x0020 (space)	0x0000 (NoSymbol)	0x0020 (space)	0x0000 (NoSymbol)	0x0020 (space)	
     66    	0xffe3 (Control_L)	
     67    	0xffbe (F1)	0x1008fe01 (XF86_Switch_VT_1)	0xffbe (F1)	0x1008fe01 (XF86_Switch_VT_1)	0xffbe (F1)	0x1008fe01 (XF86_Switch_VT_1)	
     68    	0xffbf (F2)	0x1008fe02 (XF86_Switch_VT_2)	0xffbf (F2)	0x1008fe02 (XF86_Switch_VT_2)	0xffbf (F2)	0x1008fe02 (XF86_Switch_VT_2)	
     69    	0xffc0 (F3)	0x1008fe03 (XF86_Switch_VT_3)	0xffc0 (F3)	0x1008fe03 (XF86_Switch_VT_3)	0xffc0 (F3)	0x1008fe03 (XF86_Switch_VT_3)	
     70    	0xffc1 (F4)	0x1008fe04 (XF86_Switch_VT_4)	0xffc1 (F4)	0x1008fe04 (XF86_Switch_VT_4)	0xffc1 (F4)	0x1008fe04 (XF86_Switch_VT_4)	
     71    	0xffc2 (F5)	0x1008fe05 (XF86_Switch_VT_5)	0xffc2 (F5)	0x1008fe05 (XF86_Switch_VT_5)	0xffc2 (F5)	0x1008fe05 (XF86_Switch_VT_5)	
     72    	0xffc3 (F6)	0x1008fe06 (XF86_Switch_VT_6)	0xffc3 (F6)	0x1008fe06 (XF86_Switch_VT_6)	0xffc3 (F6)	0x1008fe06 (XF86_Switch_VT_6)	
     73    	0xffc4 (F7)	0x1008fe07 (XF86_Switch_VT_7)	0xffc4 (F7)	0x1008fe07 (XF86_Switch_VT_7)	0xffc4 (F7)	0x1008fe07 (XF86_Switch_VT_7)	
     74    	0xffc5 (F8)	0x1008fe08 (XF86_Switch_VT_8)	0xffc5 (F8)	0x1008fe08 (XF86_Switch_VT_8)	0xffc5 (F8)	0x1008fe08 (XF86_Switch_VT_8)	
     75    	0xffc6 (F9)	0x1008fe09 (XF86_Switch_VT_9)	0xffc6 (F9)	0x1008fe09 (XF86_Switch_VT_9)	0xffc6 (F9)	0x1008fe09 (XF86_Switch_VT_9)	
     76    	0xffc7 (F10)	0x1008fe0a (XF86_Switch_VT_10)	0xffc7 (F10)	0x1008fe0a (XF86_Switch_VT_10)	0xffc7 (F10)	0x1008fe0a (XF86_Switch_VT_10)	
     77    	0xff7f (Num_Lock)	0xfef9 (Pointer_EnableKeys)	0xff7f (Num_Lock)	0xfef9 (Pointer_EnableKeys)	0xff7f (Num_Lock)	0xfef9 (Pointer_EnableKeys)	
     78    	0xff14 (Scroll_Lock)	0x0000 (NoSymbol)	0xff14 (Scroll_Lock)	0x0000 (NoSymbol)	0xff14 (Scroll_Lock)	
     79    	0xff95 (KP_Home)	0xffb7 (KP_7)	0xff95 (KP_Home)	0xffb7 (KP_7)	0x003c (less)	0x1002196 (U2196)	
     80    	0xff97 (KP_Up)	0xffb8 (KP_8)	0xff97 (KP_Up)	0xffb8 (KP_8)	0x003e (greater)	0x1002191 (U2191)	
     81    	0xff9a (KP_Prior)	0xffb9 (KP_9)	0xff9a (KP_Prior)	0xffb9 (KP_9)	0x005e (asciicircum)	0x1002197 (U2197)	
     82    	0xffad (KP_Subtract)	0x1002212 (U2212)	0xffad (KP_Subtract)	0x1002212 (U2212)	0x1002212 (U2212)	0x1008fe23 (XF86_Prev_VMode)	
     83    	0xff96 (KP_Left)	0xffb4 (KP_4)	0xff96 (KP_Left)	0xffb4 (KP_4)	0x005b (bracketleft)	0x1002190 (U2190)	
     84    	0xff9d (KP_Begin)	0xffb5 (KP_5)	0xff9d (KP_Begin)	0xffb5 (KP_5)	0x005d (bracketright)	0x1002194 (U2194)	
     85    	0xff98 (KP_Right)	0xffb6 (KP_6)	0xff98 (KP_Right)	0xffb6 (KP_6)	0x0024 (dollar)	0x1002192 (U2192)	
     86    	0xffab (KP_Add)	0x100002b (no name)	0xffab (KP_Add)	0x100002b (no name)	0x100002b (no name)	0x1008fe22 (XF86_Next_VMode)	
     87    	0xff9c (KP_End)	0xffb1 (KP_1)	0xff9c (KP_End)	0xffb1 (KP_1)	0x0026 (ampersand)	0x1002199 (U2199)	
     88    	0xff99 (KP_Down)	0xffb2 (KP_2)	0xff99 (KP_Down)	0xffb2 (KP_2)	0x0040 (at)	0x1002193 (U2193)	
     89    	0xff9b (KP_Next)	0xffb3 (KP_3)	0xff9b (KP_Next)	0xffb3 (KP_3)	0x0023 (numbersign)	0x1002198 (U2198)	
     90    	0xff9e (KP_Insert)	0xffb0 (KP_0)	0xff9e (KP_Insert)	0xffb0 (KP_0)	0x0027 (apostrophe)	0x1002195 (U2195)	
     91    	0xff9f (KP_Delete)	0x002e (period)	0xff9f (KP_Delete)	0x002e (period)	0x002c (comma)	0x100202f (U202F)	
     92    	0xfe03 (ISO_Level3_Shift)	0x0000 (NoSymbol)	0xfe03 (ISO_Level3_Shift)	0x0000 (NoSymbol)	0xfe03 (ISO_Level3_Shift)	
     93    	
     94    	0x003c (less)	0x003e (greater)	0x003c (less)	0x003e (greater)	0x007c (bar)	0x00a6 (brokenbar)	
     95    	0xffc8 (F11)	0x1008fe0b (XF86_Switch_VT_11)	0xffc8 (F11)	0x1008fe0b (XF86_Switch_VT_11)	0xffc8 (F11)	0x1008fe0b (XF86_Switch_VT_11)	
     96    	0xffc9 (F12)	0x1008fe0c (XF86_Switch_VT_12)	0xffc9 (F12)	0x1008fe0c (XF86_Switch_VT_12)	0xffc9 (F12)	0x1008fe0c (XF86_Switch_VT_12)	
     97    	
     98    	0xff26 (Katakana)	0x0000 (NoSymbol)	0xff26 (Katakana)	0x0000 (NoSymbol)	0xff26 (Katakana)	
     99    	0xff25 (Hiragana)	0x0000 (NoSymbol)	0xff25 (Hiragana)	0x0000 (NoSymbol)	0xff25 (Hiragana)	
    100    	0xff23 (Henkan_Mode)	0x0000 (NoSymbol)	0xff23 (Henkan_Mode)	0x0000 (NoSymbol)	0xff23 (Henkan_Mode)	
    101    	0xff27 (Hiragana_Katakana)	0x0000 (NoSymbol)	0xff27 (Hiragana_Katakana)	0x0000 (NoSymbol)	0xff27 (Hiragana_Katakana)	
    102    	0xff22 (Muhenkan)	0x0000 (NoSymbol)	0xff22 (Muhenkan)	0x0000 (NoSymbol)	0xff22 (Muhenkan)	
    103    	
    104    	0xff8d (KP_Enter)	0x0000 (NoSymbol)	0xff8d (KP_Enter)	0x0000 (NoSymbol)	0xff8d (KP_Enter)	
    105    	0xffe4 (Control_R)	
    106    	0xffaf (KP_Divide)	0x1002215 (U2215)	0xffaf (KP_Divide)	0x1002215 (U2215)	0x10000f7 (no name)	0x1008fe20 (XF86_Ungrab)	
    107    	0xff61 (Print)	0xff15 (Sys_Req)	0xff61 (Print)	0xff15 (Sys_Req)	0xff61 (Print)	0xff15 (Sys_Req)	
    108    	0xffea (Alt_R)	
    109    	0xff0a (Linefeed)	0x0000 (NoSymbol)	0xff0a (Linefeed)	0x0000 (NoSymbol)	0xff0a (Linefeed)	
    110    	0xff50 (Home)	0x0000 (NoSymbol)	0xff50 (Home)	0x0000 (NoSymbol)	0xff50 (Home)	
    111    	0xff52 (Up)	
    112    	0xff55 (Prior)	0x0000 (NoSymbol)	0xff55 (Prior)	0x0000 (NoSymbol)	0xff55 (Prior)	
    113    	0xff51 (Left)	
    114    	0xff53 (Right)	
    115    	0xff57 (End)	0x0000 (NoSymbol)	0xff57 (End)	0x0000 (NoSymbol)	0xff57 (End)	
    116    	0xff54 (Down)	
    117    	0xff56 (Next)	0x0000 (NoSymbol)	0xff56 (Next)	0x0000 (NoSymbol)	0xff56 (Next)	
    118    	0xff63 (Insert)	0x0000 (NoSymbol)	0xff63 (Insert)	0x0000 (NoSymbol)	0xff63 (Insert)	
    119    	0xffff (Delete)	
    120    	
    121    	0x1008ff12 (XF86AudioMute)	0x0000 (NoSymbol)	0x1008ff12 (XF86AudioMute)	0x0000 (NoSymbol)	0x1008ff12 (XF86AudioMute)	
    122    	0x1008ff11 (XF86AudioLowerVolume)	0x0000 (NoSymbol)	0x1008ff11 (XF86AudioLowerVolume)	0x0000 (NoSymbol)	0x1008ff11 (XF86AudioLowerVolume)	
    123    	0x1008ff13 (XF86AudioRaiseVolume)	0x0000 (NoSymbol)	0x1008ff13 (XF86AudioRaiseVolume)	0x0000 (NoSymbol)	0x1008ff13 (XF86AudioRaiseVolume)	
    124    	0x1008ff2a (XF86PowerOff)	0x0000 (NoSymbol)	0x1008ff2a (XF86PowerOff)	0x0000 (NoSymbol)	0x1008ff2a (XF86PowerOff)	
    125    	0xffbd (KP_Equal)	0x0000 (NoSymbol)	0xffbd (KP_Equal)	0x0000 (NoSymbol)	0xffbd (KP_Equal)	
    126    	0x00b1 (plusminus)	0x0000 (NoSymbol)	0x00b1 (plusminus)	0x0000 (NoSymbol)	0x00b1 (plusminus)	
    127    	0xff20 (Multi_key)	
    128    	
    129    	0xffae (KP_Decimal)	0x0000 (NoSymbol)	0xffae (KP_Decimal)	0x0000 (NoSymbol)	0xffae (KP_Decimal)	
    130    	0xff31 (Hangul)	0x0000 (NoSymbol)	0xff31 (Hangul)	0x0000 (NoSymbol)	0xff31 (Hangul)	
    131    	0xff34 (Hangul_Hanja)	0x0000 (NoSymbol)	0xff34 (Hangul_Hanja)	0x0000 (NoSymbol)	0xff34 (Hangul_Hanja)	
    132    	
    133    	0xff7e (Mode_switch)	
    134    	0xffec (Super_R)	0x0000 (NoSymbol)	0xffec (Super_R)	0x0000 (NoSymbol)	0xffec (Super_R)	
    135    	0xffe8 (Meta_R)	
    136    	0xff69 (Cancel)	0x0000 (NoSymbol)	0xff69 (Cancel)	0x0000 (NoSymbol)	0xff69 (Cancel)	
    137    	0xff66 (Redo)	0x0000 (NoSymbol)	0xff66 (Redo)	0x0000 (NoSymbol)	0xff66 (Redo)	
    138    	0x1005ff70 (SunProps)	0x0000 (NoSymbol)	0x1005ff70 (SunProps)	0x0000 (NoSymbol)	0x1005ff70 (SunProps)	
    139    	0xff65 (Undo)	0x0000 (NoSymbol)	0xff65 (Undo)	0x0000 (NoSymbol)	0xff65 (Undo)	
    140    	0x1005ff71 (SunFront)	0x0000 (NoSymbol)	0x1005ff71 (SunFront)	0x0000 (NoSymbol)	0x1005ff71 (SunFront)	
    141    	0x1008ff57 (XF86Copy)	0x0000 (NoSymbol)	0x1008ff57 (XF86Copy)	0x0000 (NoSymbol)	0x1008ff57 (XF86Copy)	
    142    	0x1005ff73 (SunOpen)	0x0000 (NoSymbol)	0x1005ff73 (SunOpen)	0x0000 (NoSymbol)	0x1005ff73 (SunOpen)	
    143    	0x1008ff6d (XF86Paste)	0x0000 (NoSymbol)	0x1008ff6d (XF86Paste)	0x0000 (NoSymbol)	0x1008ff6d (XF86Paste)	
    144    	0xff68 (Find)	0x0000 (NoSymbol)	0xff68 (Find)	0x0000 (NoSymbol)	0xff68 (Find)	
    145    	0x1008ff58 (XF86Cut)	0x0000 (NoSymbol)	0x1008ff58 (XF86Cut)	0x0000 (NoSymbol)	0x1008ff58 (XF86Cut)	
    146    	0xff6a (Help)	0x0000 (NoSymbol)	0xff6a (Help)	0x0000 (NoSymbol)	0xff6a (Help)	
    147    	0x1008ff65 (XF86MenuKB)	0x0000 (NoSymbol)	0x1008ff65 (XF86MenuKB)	0x0000 (NoSymbol)	0x1008ff65 (XF86MenuKB)	
    148    	0x1008ff1d (XF86Calculator)	0x0000 (NoSymbol)	0x1008ff1d (XF86Calculator)	0x0000 (NoSymbol)	0x1008ff1d (XF86Calculator)	
    149    	
    150    	0x1008ff2f (XF86Sleep)	0x0000 (NoSymbol)	0x1008ff2f (XF86Sleep)	0x0000 (NoSymbol)	0x1008ff2f (XF86Sleep)	
    151    	0x1008ff2b (XF86WakeUp)	0x0000 (NoSymbol)	0x1008ff2b (XF86WakeUp)	0x0000 (NoSymbol)	0x1008ff2b (XF86WakeUp)	
    152    	0x1008ff5d (XF86Explorer)	0x0000 (NoSymbol)	0x1008ff5d (XF86Explorer)	0x0000 (NoSymbol)	0x1008ff5d (XF86Explorer)	
    153    	0x1008ff7b (XF86Send)	0x0000 (NoSymbol)	0x1008ff7b (XF86Send)	0x0000 (NoSymbol)	0x1008ff7b (XF86Send)	
    154    	
    155    	0x1008ff8a (XF86Xfer)	0x0000 (NoSymbol)	0x1008ff8a (XF86Xfer)	0x0000 (NoSymbol)	0x1008ff8a (XF86Xfer)	
    156    	0x1008ff41 (XF86Launch1)	0x0000 (NoSymbol)	0x1008ff41 (XF86Launch1)	0x0000 (NoSymbol)	0x1008ff41 (XF86Launch1)	
    157    	0x1008ff42 (XF86Launch2)	0x0000 (NoSymbol)	0x1008ff42 (XF86Launch2)	0x0000 (NoSymbol)	0x1008ff42 (XF86Launch2)	
    158    	0x1008ff2e (XF86WWW)	0x0000 (NoSymbol)	0x1008ff2e (XF86WWW)	0x0000 (NoSymbol)	0x1008ff2e (XF86WWW)	
    159    	0x1008ff5a (XF86DOS)	0x0000 (NoSymbol)	0x1008ff5a (XF86DOS)	0x0000 (NoSymbol)	0x1008ff5a (XF86DOS)	
    160    	0x1008ff2d (XF86ScreenSaver)	0x0000 (NoSymbol)	0x1008ff2d (XF86ScreenSaver)	0x0000 (NoSymbol)	0x1008ff2d (XF86ScreenSaver)	
    161    	
    162    	0x1008ff74 (XF86RotateWindows)	0x0000 (NoSymbol)	0x1008ff74 (XF86RotateWindows)	0x0000 (NoSymbol)	0x1008ff74 (XF86RotateWindows)	
    163    	0x1008ff19 (XF86Mail)	0x0000 (NoSymbol)	0x1008ff19 (XF86Mail)	0x0000 (NoSymbol)	0x1008ff19 (XF86Mail)	
    164    	0x1008ff30 (XF86Favorites)	0x0000 (NoSymbol)	0x1008ff30 (XF86Favorites)	0x0000 (NoSymbol)	0x1008ff30 (XF86Favorites)	
    165    	0x1008ff33 (XF86MyComputer)	0x0000 (NoSymbol)	0x1008ff33 (XF86MyComputer)	0x0000 (NoSymbol)	0x1008ff33 (XF86MyComputer)	
    166    	0x1008ff26 (XF86Back)	0x0000 (NoSymbol)	0x1008ff26 (XF86Back)	0x0000 (NoSymbol)	0x1008ff26 (XF86Back)	
    167    	0x1008ff27 (XF86Forward)	0x0000 (NoSymbol)	0x1008ff27 (XF86Forward)	0x0000 (NoSymbol)	0x1008ff27 (XF86Forward)	
    168    	
    169    	0x1008ff2c (XF86Eject)	0x0000 (NoSymbol)	0x1008ff2c (XF86Eject)	0x0000 (NoSymbol)	0x1008ff2c (XF86Eject)	
    170    	0x1008ff2c (XF86Eject)	0x1008ff2c (XF86Eject)	0x1008ff2c (XF86Eject)	0x1008ff2c (XF86Eject)	0x1008ff2c (XF86Eject)	0x1008ff2c (XF86Eject)	
    171    	0x1008ff17 (XF86AudioNext)	0x0000 (NoSymbol)	0x1008ff17 (XF86AudioNext)	0x0000 (NoSymbol)	0x1008ff17 (XF86AudioNext)	
    172    	0x1008ff14 (XF86AudioPlay)	0x1008ff31 (XF86AudioPause)	0x1008ff14 (XF86AudioPlay)	0x1008ff31 (XF86AudioPause)	0x1008ff14 (XF86AudioPlay)	0x1008ff31 (XF86AudioPause)	
    173    	0x1008ff16 (XF86AudioPrev)	0x0000 (NoSymbol)	0x1008ff16 (XF86AudioPrev)	0x0000 (NoSymbol)	0x1008ff16 (XF86AudioPrev)	
    174    	0x1008ff15 (XF86AudioStop)	0x1008ff2c (XF86Eject)	0x1008ff15 (XF86AudioStop)	0x1008ff2c (XF86Eject)	0x1008ff15 (XF86AudioStop)	0x1008ff2c (XF86Eject)	
    175    	0x1008ff1c (XF86AudioRecord)	0x0000 (NoSymbol)	0x1008ff1c (XF86AudioRecord)	0x0000 (NoSymbol)	0x1008ff1c (XF86AudioRecord)	
    176    	0x1008ff3e (XF86AudioRewind)	0x0000 (NoSymbol)	0x1008ff3e (XF86AudioRewind)	0x0000 (NoSymbol)	0x1008ff3e (XF86AudioRewind)	
    177    	0x1008ff6e (XF86Phone)	0x0000 (NoSymbol)	0x1008ff6e (XF86Phone)	0x0000 (NoSymbol)	0x1008ff6e (XF86Phone)	
    178    	
    179    	0x1008ff81 (XF86Tools)	0x0000 (NoSymbol)	0x1008ff81 (XF86Tools)	0x0000 (NoSymbol)	0x1008ff81 (XF86Tools)	
    180    	0x1008ff18 (XF86HomePage)	0x0000 (NoSymbol)	0x1008ff18 (XF86HomePage)	0x0000 (NoSymbol)	0x1008ff18 (XF86HomePage)	
    181    	0x1008ff73 (XF86Reload)	0x0000 (NoSymbol)	0x1008ff73 (XF86Reload)	0x0000 (NoSymbol)	0x1008ff73 (XF86Reload)	
    182    	0x1008ff56 (XF86Close)	0x0000 (NoSymbol)	0x1008ff56 (XF86Close)	0x0000 (NoSymbol)	0x1008ff56 (XF86Close)	
    183    	
    184    	
    185    	0x1008ff78 (XF86ScrollUp)	0x0000 (NoSymbol)	0x1008ff78 (XF86ScrollUp)	0x0000 (NoSymbol)	0x1008ff78 (XF86ScrollUp)	
    186    	0x1008ff79 (XF86ScrollDown)	0x0000 (NoSymbol)	0x1008ff79 (XF86ScrollDown)	0x0000 (NoSymbol)	0x1008ff79 (XF86ScrollDown)	
    187    	0x0028 (parenleft)	0x0000 (NoSymbol)	0x0028 (parenleft)	0x0000 (NoSymbol)	0x0028 (parenleft)	
    188    	0x0029 (parenright)	0x0000 (NoSymbol)	0x0029 (parenright)	0x0000 (NoSymbol)	0x0029 (parenright)	
    189    	0x1008ff68 (XF86New)	0x0000 (NoSymbol)	0x1008ff68 (XF86New)	0x0000 (NoSymbol)	0x1008ff68 (XF86New)	
    190    	0xff66 (Redo)	0x0000 (NoSymbol)	0xff66 (Redo)	0x0000 (NoSymbol)	0xff66 (Redo)	
    191    	
    192    	
    193    	
    194    	
    195    	
    196    	
    197    	
    198    	
    199    	
    200    	
    201    	
    202    	
    203    	0xff7e (Mode_switch)	0x0000 (NoSymbol)	0xff7e (Mode_switch)	0x0000 (NoSymbol)	0xff7e (Mode_switch)	
    204    	0x0000 (NoSymbol)	0xffe9 (Alt_L)	0x0000 (NoSymbol)	0xffe9 (Alt_L)	0x0000 (NoSymbol)	0xffe9 (Alt_L)	
    205    	0x0000 (NoSymbol)	0xffe7 (Meta_L)	0x0000 (NoSymbol)	0xffe7 (Meta_L)	0x0000 (NoSymbol)	0xffe7 (Meta_L)	
    206    	0x0000 (NoSymbol)	0xffeb (Super_L)	0x0000 (NoSymbol)	0xffeb (Super_L)	0x0000 (NoSymbol)	0xffeb (Super_L)	
    207    	0x0000 (NoSymbol)	0xffed (Hyper_L)	0x0000 (NoSymbol)	0xffed (Hyper_L)	0x0000 (NoSymbol)	0xffed (Hyper_L)	
    208    	0x1008ff14 (XF86AudioPlay)	0x0000 (NoSymbol)	0x1008ff14 (XF86AudioPlay)	0x0000 (NoSymbol)	0x1008ff14 (XF86AudioPlay)	
    209    	0x1008ff31 (XF86AudioPause)	0x0000 (NoSymbol)	0x1008ff31 (XF86AudioPause)	0x0000 (NoSymbol)	0x1008ff31 (XF86AudioPause)	
    210    	0x1008ff43 (XF86Launch3)	0x0000 (NoSymbol)	0x1008ff43 (XF86Launch3)	0x0000 (NoSymbol)	0x1008ff43 (XF86Launch3)	
    211    	0x1008ff44 (XF86Launch4)	0x0000 (NoSymbol)	0x1008ff44 (XF86Launch4)	0x0000 (NoSymbol)	0x1008ff44 (XF86Launch4)	
    212    	
    213    	0x1008ffa7 (XF86Suspend)	0x0000 (NoSymbol)	0x1008ffa7 (XF86Suspend)	0x0000 (NoSymbol)	0x1008ffa7 (XF86Suspend)	
    214    	0x1008ff56 (XF86Close)	0x0000 (NoSymbol)	0x1008ff56 (XF86Close)	0x0000 (NoSymbol)	0x1008ff56 (XF86Close)	
    215    	0x1008ff14 (XF86AudioPlay)	0x0000 (NoSymbol)	0x1008ff14 (XF86AudioPlay)	0x0000 (NoSymbol)	0x1008ff14 (XF86AudioPlay)	
    216    	0x1008ff27 (XF86Forward)	0x0000 (NoSymbol)	0x1008ff27 (XF86Forward)	0x0000 (NoSymbol)	0x1008ff27 (XF86Forward)	
    217    	
    218    	0xff61 (Print)	0x0000 (NoSymbol)	0xff61 (Print)	0x0000 (NoSymbol)	0xff61 (Print)	
    219    	
    220    	0x1008ff8f (XF86WebCam)	0x0000 (NoSymbol)	0x1008ff8f (XF86WebCam)	0x0000 (NoSymbol)	0x1008ff8f (XF86WebCam)	
    221    	
    222    	
    223    	0x1008ff19 (XF86Mail)	0x0000 (NoSymbol)	0x1008ff19 (XF86Mail)	0x0000 (NoSymbol)	0x1008ff19 (XF86Mail)	
    224    	
    225    	0x1008ff1b (XF86Search)	0x0000 (NoSymbol)	0x1008ff1b (XF86Search)	0x0000 (NoSymbol)	0x1008ff1b (XF86Search)	
    226    	
    227    	0x1008ff3c (XF86Finance)	0x0000 (NoSymbol)	0x1008ff3c (XF86Finance)	0x0000 (NoSymbol)	0x1008ff3c (XF86Finance)	
    228    	
    229    	0x1008ff36 (XF86Shop)	0x0000 (NoSymbol)	0x1008ff36 (XF86Shop)	0x0000 (NoSymbol)	0x1008ff36 (XF86Shop)	
    230    	
    231    	0xff69 (Cancel)	0x0000 (NoSymbol)	0xff69 (Cancel)	0x0000 (NoSymbol)	0xff69 (Cancel)	
    232    	0x1008ff03 (XF86MonBrightnessDown)	0x0000 (NoSymbol)	0x1008ff03 (XF86MonBrightnessDown)	0x0000 (NoSymbol)	0x1008ff03 (XF86MonBrightnessDown)	
    233    	0x1008ff02 (XF86MonBrightnessUp)	0x0000 (NoSymbol)	0x1008ff02 (XF86MonBrightnessUp)	0x0000 (NoSymbol)	0x1008ff02 (XF86MonBrightnessUp)	
    234    	0x1008ff32 (XF86AudioMedia)	0x0000 (NoSymbol)	0x1008ff32 (XF86AudioMedia)	0x0000 (NoSymbol)	0x1008ff32 (XF86AudioMedia)	
    235    	0x1008ff59 (XF86Display)	0x0000 (NoSymbol)	0x1008ff59 (XF86Display)	0x0000 (NoSymbol)	0x1008ff59 (XF86Display)	
    236    	0x1008ff04 (XF86KbdLightOnOff)	0x0000 (NoSymbol)	0x1008ff04 (XF86KbdLightOnOff)	0x0000 (NoSymbol)	0x1008ff04 (XF86KbdLightOnOff)	
    237    	0x1008ff06 (XF86KbdBrightnessDown)	0x0000 (NoSymbol)	0x1008ff06 (XF86KbdBrightnessDown)	0x0000 (NoSymbol)	0x1008ff06 (XF86KbdBrightnessDown)	
    238    	0x1008ff05 (XF86KbdBrightnessUp)	0x0000 (NoSymbol)	0x1008ff05 (XF86KbdBrightnessUp)	0x0000 (NoSymbol)	0x1008ff05 (XF86KbdBrightnessUp)	
    239    	0x1008ff7b (XF86Send)	0x0000 (NoSymbol)	0x1008ff7b (XF86Send)	0x0000 (NoSymbol)	0x1008ff7b (XF86Send)	
    240    	0x1008ff72 (XF86Reply)	0x0000 (NoSymbol)	0x1008ff72 (XF86Reply)	0x0000 (NoSymbol)	0x1008ff72 (XF86Reply)	
    241    	0x1008ff90 (XF86MailForward)	0x0000 (NoSymbol)	0x1008ff90 (XF86MailForward)	0x0000 (NoSymbol)	0x1008ff90 (XF86MailForward)	
    242    	0x1008ff77 (XF86Save)	0x0000 (NoSymbol)	0x1008ff77 (XF86Save)	0x0000 (NoSymbol)	0x1008ff77 (XF86Save)	
    243    	0x1008ff5b (XF86Documents)	0x0000 (NoSymbol)	0x1008ff5b (XF86Documents)	0x0000 (NoSymbol)	0x1008ff5b (XF86Documents)	
    244    	0x1008ff93 (XF86Battery)	0x0000 (NoSymbol)	0x1008ff93 (XF86Battery)	0x0000 (NoSymbol)	0x1008ff93 (XF86Battery)	
    245    	0x1008ff94 (XF86Bluetooth)	0x0000 (NoSymbol)	0x1008ff94 (XF86Bluetooth)	0x0000 (NoSymbol)	0x1008ff94 (XF86Bluetooth)	
    246    	0x1008ff95 (XF86WLAN)	0x0000 (NoSymbol)	0x1008ff95 (XF86WLAN)	0x0000 (NoSymbol)	0x1008ff95 (XF86WLAN)	
    247    	
    248    	
    249    	
    250    	
    251    	
    252    	
    253    	
    254    	
    255    	

```

---


---
title: "nvidia sauerbraten problems"
date: 2007-12-13
forum: Gaming &amp; Leisure
---

### Post by evaderus on 2007-12-13
I've been trying to figure out this problem for the past hour and I finally just gave up. I've had compiz fusion running great, but when it comes to sauerbraten I don't have 3d support for some reason?

here is what the terminal says:
```
dave@ubuntustudio:~$ sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: console
init: gl
Renderer: GeForce 7600 GT/PCI/SSE2/3DNOW! (NVIDIA Corporation)
Driver: 1.2 (2.1.0 NVIDIA 96.39)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
Rendering using the OpenGL 1.5 assembly shader path.
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No texture rectangle support. (no full screen shaders)
WARNING: No framebuffer object support. (reflective water may be slow)
init: world
init: sound
init: cfg
Could not set gamma (card/driver doesn't support it?)
sdl: Gamma correction not supported on this visual
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.1 seconds)
Mining Station by metlslime
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  1018
  Current serial number in output stream:  1020
dave@ubuntustudio:~$ 
```

and here is my xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce 7600 GT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 7600 GT"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by evaderus on 2007-12-13
ok while I was waiting for a reply I tried installing the driver supplied by nvidia and now X won't start. I even tried using my backed up xorg.conf file and still no go. I probably need to go in and manually fix my xorg.conf, or update it or something. I don't really know what to do or how. Please help

---

### Post by hotdoog on 2007-12-15
I don't have any help except to say that I have the same problem... Sorta... Well my output is the same.

```
...X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  777
  Current serial number in output stream:  779
```

Actually my real problem is definately different. I'm trying to run sauerbraten on my downstairs computer through ssh over our home network. My graphics card downstairs is ATI Radeon. I was thinking maybe the differance in display output number was the issue because it was confused by my forwarding X to a different computer and graphics card. My upstairs computer - which does run sauerbraten fine right now - does have an nVidia card. Also this downstairs computer is a lot slower - it can't handle sauerbraten except with the processes running on my faster machine. So it could just be some capacity issue?

Anyways, that's all probably just more useless details to you but perhaps it will spark an idea from someone who understands the problem.

cheers!

---


---
title: "Planets black not textured in space-orbit game"
date: 2010-11-16
forum: Gaming &amp; Leisure
---

### Post by sclagler on 2010-11-16
****
Greetings!

I am a neophyte to computer gaming and can't figure out how to make the planets and moons visible.  I can crash into them so they're not "hidden".

According to the orbit.log the textures SEEM to load upon start of the game.

I am using space-orbit 1.01-10build1 on ubuntu 10.10 64 bit.

I am using nvidia driver 260.19.06 64bit.

I am using 2 nvidia gts250 video cards in sli.

The following is the orbit.log for the first few seconds of play.




```

Tue Nov 16 01:09:54 2010: InitLog()
Tue Nov 16 01:09:54 2010: InitStuff: ORBIT Version 1.01
Tue Nov 16 01:09:54 2010: ReadPrefs: Reading preferences file
Tue Nov 16 01:09:54 2010: ReadPrefs: mission train01.msn
Tue Nov 16 01:09:54 2010: ReadPrefs: screenwidth 1280
Tue Nov 16 01:09:54 2010: ReadPrefs: screenheight 1024
Tue Nov 16 01:09:54 2010: ReadPrefs: fullscreen 1
Tue Nov 16 01:09:54 2010: ReadPrefs: gamemode no
Tue Nov 16 01:09:54 2010: ReadPrefs: name Sparky
Tue Nov 16 01:09:54 2010: ReadPrefs: model light2.tri
Tue Nov 16 01:09:54 2010: ReadPrefs: vulnerable 1
Tue Nov 16 01:09:54 2010: ReadPrefs: fov 90.000000
Tue Nov 16 01:09:54 2010: ReadPrefs: joy_throttle 1
Tue Nov 16 01:09:54 2010: ReadPrefs: deadzone 0.100000
Tue Nov 16 01:09:54 2010: ReadPrefs: starfield 2
Tue Nov 16 01:09:54 2010: ReadPrefs: drawhud 1
Tue Nov 16 01:09:54 2010: ReadPrefs: showfps 1
Tue Nov 16 01:09:54 2010: ReadPrefs: gravity 0
Tue Nov 16 01:09:54 2010: ReadPrefs: draw_orbits 0
Tue Nov 16 01:09:54 2010: ReadPrefs: orbit 0
Tue Nov 16 01:09:54 2010: ReadPrefs: compression 1.000000
Tue Nov 16 01:09:54 2010: ReadPrefs: junk 1
Tue Nov 16 01:09:54 2010: ReadPrefs: sound 1
Tue Nov 16 01:09:54 2010: ReadPrefs: show_names 1
Tue Nov 16 01:09:54 2010: ReadPrefs: screen_shot_num 1
Tue Nov 16 01:09:54 2010: ReadPrefs: rings 1
Tue Nov 16 01:09:54 2010: ReadPrefs: ring_sectors 32
Tue Nov 16 01:09:54 2010: ReadPrefs: textures 1
Tue Nov 16 01:09:54 2010: ReadPrefs: realdistances 0
Tue Nov 16 01:09:54 2010: ReadPrefs: weapon 0
Tue Nov 16 01:09:54 2010: ReadPrefs: mouse_control 1
Tue Nov 16 01:09:54 2010: ReadPrefs: mouse_flipx 0
Tue Nov 16 01:09:54 2010: ReadPrefs: mouse_flipy 0
Tue Nov 16 01:09:54 2010: ReadPrefs: flightmodel 0
Tue Nov 16 01:09:54 2010: ReadPrefs: fullstop 1
Tue Nov 16 01:09:54 2010: ReadPrefs: superwarp 1
Tue Nov 16 01:09:54 2010: ReadPrefs: port 2061
Tue Nov 16 01:09:54 2010: ReadPrefs: posx -1999.391670
Tue Nov 16 01:09:54 2010: ReadPrefs: posy 1493.028890
Tue Nov 16 01:09:54 2010: ReadPrefs: posz 0.000000
Tue Nov 16 01:09:54 2010: ReadPrefs: slices0 7
Tue Nov 16 01:09:54 2010: ReadPrefs: stacks0 3
Tue Nov 16 01:09:54 2010: ReadPrefs: slices1 13
Tue Nov 16 01:09:54 2010: ReadPrefs: stacks1 6
Tue Nov 16 01:09:54 2010: ReadPrefs: slices2 24
Tue Nov 16 01:09:54 2010: ReadPrefs: stacks2 12
Tue Nov 16 01:09:54 2010: OpenWindow: OpenGL vendor: NVIDIA Corporation
Tue Nov 16 01:09:54 2010: OpenWindow: OpenGL renderer: GeForce GTS 250/PCI/SSE2
Tue Nov 16 01:09:54 2010: OpenWindow: OpenGL version: 3.3.0 NVIDIA 260.19.06
Tue Nov 16 01:09:54 2010: RandomPlanets: Randomizing planets
Tue Nov 16 01:09:54 2010: ResetPlanets: resetting planets
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file mercury.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file venus.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file earth.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file moon.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file mars.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file phobos.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file deimos.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file jupiter.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file io.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file europa.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file ganymede.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file callisto.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file saturn.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file mimas.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file enceladus.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file tethys.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file dione.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file rhea.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file titan.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file iapetus.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file uranus.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file miranda.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file ariel.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file umbriel.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file titania.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file oberon.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file neptune.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file triton.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file proteus.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file pluto.ppm
Tue Nov 16 01:09:54 2010: ReadPlanetTexture: Reading texture file charon.ppm
Tue Nov 16 01:09:54 2010: InitNetwork: Initializing network
Tue Nov 16 01:09:54 2010: ReadMission: reading missions/train01.msn
Tue Nov 16 01:09:54 2010: ResetPlanets: resetting planets
Tue Nov 16 01:09:54 2010: Cursor: Setting cursor to Earth
Tue Nov 16 01:09:54 2010: Cursor: (Set cursor to 1627.284636 -1889.088755 0.000000)
Tue Nov 16 01:09:54 2010: Set cursor to 1624.784636 -1889.088755 0.000000
Tue Nov 16 01:09:54 2010: Player: Set player position to 1624.784636 -1889.088755 0.000000
Tue Nov 16 01:09:54 2010: Briefing:  Training Mission #01: One small step\\ In this training session you will learn how to move your ship using your low-speed engines.\\ Your objective is to fly from Earth orbit to the Moon and back again.\\ Follow the instructions which will appear on the screen.\\ Briefing concluded. Good luck, sir!\\ You may press 'M' to remove this message from your screen.\\ Press 'B' at any time to see this briefing again.
Tue Nov 16 01:09:54 2010: Event: Creating event 0
Tue Nov 16 01:09:54 2010: EvName: Event 0 named e1
Tue Nov 16 01:09:54 2010: EvTrigger: Setting event 0 trigger to Alarm
Tue Nov 16 01:09:54 2010: EvValue: Event 0 trigger value set to 30.0
Tue Nov 16 01:09:54 2010: EvAction: Setting event 0.0 action to Message
Tue Nov 16 01:09:54 2010: EvValue: Event 0.0 action set to  Press 'N' to see the names of objects and planets.\\ Use the joystick to point your ship toward the moon.\\ Then hold 'A' to accelerate toward the moon.\\ Your current velocity is shown to the left of the HUD. Increase speed to about 10000 kps.
Tue Nov 16 01:09:54 2010: Cursor: Setting cursor to Earth
Tue Nov 16 01:09:54 2010: Cursor: (Set cursor to 1627.284636 -1889.088755 0.000000)
Tue Nov 16 01:09:54 2010: Event: Creating event 1
Tue Nov 16 01:09:54 2010: EvTrigger: Setting event 1 trigger to Depart
Tue Nov 16 01:09:54 2010: EvValue: Event 1 trigger value set to 20000.0
Tue Nov 16 01:09:54 2010: EvAction: Setting event 1.0 action to Message
Tue Nov 16 01:09:54 2010: EvValue: Event 1.0 action set to  You can use 'Z' to slow down.\\ You can use SPACE to come to a full stop.
Tue Nov 16 01:09:54 2010: EvAction: Setting event 1.1 action to Disable
Tue Nov 16 01:09:54 2010: EvValue: Event 1.1 action set to e1
Tue Nov 16 01:09:54 2010: Cursor: Setting cursor to Moon
Tue Nov 16 01:09:54 2010: Cursor: (Set cursor to 1686.189623 -1912.201973 -10.025939)
Tue Nov 16 01:09:54 2010: Event: Creating event 2
Tue Nov 16 01:09:54 2010: EvTrigger: Setting event 2 trigger to Approach
Tue Nov 16 01:09:54 2010: EvValue: Event 2 trigger value set to 75000.0
Tue Nov 16 01:09:54 2010: EvAction: Setting event 2.0 action to Message
Tue Nov 16 01:09:54 2010: EvValue: Event 2.0 action set to  You are approaching the Moon.\\ Be prepared to stop using the SPACE key.
Tue Nov 16 01:09:54 2010: Event: Creating event 3
Tue Nov 16 01:09:54 2010: EvTrigger: Setting event 3 trigger to Approach
Tue Nov 16 01:09:54 2010: EvValue: Event 3 trigger value set to 15000.0
Tue Nov 16 01:09:54 2010: EvAction: Setting event 3.0 action to Message
Tue Nov 16 01:09:54 2010: EvValue: Event 3.0 action set to  You have reached the moon. Congratulations!\\ Now turn your ship around and head back to Earth.
Tue Nov 16 01:09:54 2010: EvAction: Setting event 3.1 action to Enable
Tue Nov 16 01:09:54 2010: EvValue: Event 3.1 action set to e2
Tue Nov 16 01:09:54 2010: Cursor: Setting cursor to Earth
Tue Nov 16 01:09:54 2010: Cursor: (Set cursor to 1627.284636 -1889.088755 0.000000)
Tue Nov 16 01:09:54 2010: Event: Creating event 4
Tue Nov 16 01:09:54 2010: EvName: Event 4 named e2
Tue Nov 16 01:09:54 2010: EvTrigger: Setting event 4 trigger to Approach
Tue Nov 16 01:09:54 2010: EvValue: Event 4 trigger value set to 20000
Tue Nov 16 01:09:54 2010: EvAction: Setting event 4.0 action to Message
Tue Nov 16 01:09:54 2010: EvValue: Event 4.0 action set to  You did it! Now you know how to maneuver your ship at low speeds.\\ Please wait a few seconds for the next training mission to begin.
Tue Nov 16 01:09:54 2010: EvAction: Setting event 4.1 action to Enable
Tue Nov 16 01:09:54 2010: EvValue: Event 4.1 action set to e3
Tue Nov 16 01:09:54 2010: EvAction: Setting event 4.2 action to Stop
Tue Nov 16 01:09:54 2010: Event: Creating event 5
Tue Nov 16 01:09:54 2010: EvName: Event 5 named e3
Tue Nov 16 01:09:54 2010: EvTrigger: Setting event 5 trigger to Alarm
Tue Nov 16 01:09:54 2010: EvValue: Event 5 trigger value set to 10.0
Tue Nov 16 01:09:54 2010: EvAction: Setting event 5.0 action to LoadMission
Tue Nov 16 01:09:54 2010: EvValue: Event 5.0 action set to train02.msn
Tue Nov 16 01:09:54 2010: ReadMission: Done reading mission
Tue Nov 16 01:09:57 2010: Escape key, exiting...
Tue Nov 16 01:09:57 2010: ShutdownNetwork: Shutting down network
Tue Nov 16 01:09:57 2010: WritePrefs: Writing preferences file
Tue Nov 16 01:09:57 2010: CloseLog()

```

Sorry about that.

thanks,
 -sheldon**[B]**[/B]

---

### Post by sclagler on 2010-11-27
anyone?

---


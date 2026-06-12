---
title: "PS3 wireless rockband drums working with python"
date: 2009-07-27
forum: Gaming &amp; Leisure
---

### Post by vash5556 on 2009-07-27
I wrote a python script today to get the wireless ps3 rockband drums working.  It uses the pygame module to use the drums as a joystick and plays sounds depending on which pad is hit.  Any comments on the code itself would be nice.  I am uploading my script with the sounds i am currently using.  Also i will post the code here for people that have their own drum sounds they want to use.  Any feedback would be appreciated.

```

#! /usr/bin/python

# This program is for interfacing with the Rock Band drum set
# It uses pygame to use the drum set as a joystick to make
# life easier.

# Drum Setup
# ----------
#
# Button:        Drum Pad:
# -------        ---------
# 2            Red Pad
# 3            Yellow Pad
# 0            Blue Pad
# 1            Green Pad
# 4            Kick Pedal
# 9            Start Button

import sys
import pygame
from pygame import locals

pygame.mixer.pre_init(44100, -16, 8, 768)

# Initialize pygame
pygame.init()

# Initialize the audio
pygame.mixer.init()

# Initialize the joystick module
pygame.joystick.init()

# Holds total number of buttons on the drumset
buttonNo = 0

# Setup the sounds
snareDrum = pygame.mixer.Sound("Sounds/snare.wav")
hihats = pygame.mixer.Sound("Sounds/hihat.wav")
bassDrum = pygame.mixer.Sound("Sounds/bass.wav")
rideCymbal = pygame.mixer.Sound("Sounds/ride.wav")
crashCymbal = pygame.mixer.Sound("Sounds/crash.wav")

print "Initializing Drumset...."
try:
    # Initialize the first joystick as the drums
    drums = pygame.joystick.Joystick(0)
    drums.init()
    print "Enabled Drums: " + drums.get_name()
    # Get the total number of buttons on the set
    buttonNo = drums.get_numbuttons()
except pygame.error:
    # The drums werent found
    print "No Drums Found!!!"
    sys.exit(2)

print "Now capturing input, press the start button on your controller to exit"
while 1:
    # Capture events into an event buffer and process the events
    for e in pygame.event.get():
        #print 'event : ' + str(e.type)
        if e.type == pygame.locals.JOYBUTTONDOWN:            
            #for button in range(buttonNo):
            #    print "Button: ", str(button), "\tState: ", str(drums.get_button(button))
            
            if drums.get_button(2):
                #print "Red Pad Hit"
                snareDrum.play()
            if drums.get_button(3):
                #print "Yellow Pad Hit"
                hihats.play()
            if drums.get_button(0):
                #print "Blue Pad Hit"
                rideCymbal.play()
            if drums.get_button(1):
                #print "Green Pad Hit"
                crashCymbal.play()
            if drums.get_button(4):
                #print "Kick Pedal Hit"
                bassDrum.play()
            if drums.get_button(9):
                print "Now Exiting!!!"
                sys.exit()

```

---

### Post by Ericj1186 on 2009-07-27
Any idea if this will make it work with Frets on Fire X?  When I would hit any pad/the bass drum, it would recognize it as Joystick 2.

---

### Post by vash5556 on 2009-07-27
> **Ericj1186 said:**
> Any idea if this will make it work with Frets on Fire X?  When I would hit any pad/the bass drum, it would recognize it as Joystick 2.
I am actually not sure, I haven't touched frets on fire in a while because the computer I used to have it on is dead, and this one can barely run it.  If anyone knows this would be interesting to find out.

---

### Post by Ericj1186 on 2009-07-27
FoFiX works with the Rock Band drumset for 360 and PS2, but I have no luck with PS2.  So, not sure.

Cool program though.

---

### Post by Flare88 on 2009-11-30
I know this thread is aging/old but I just wanted to thank vash for the program. I was able to give my rockband drums a new purpose, all within a college budget :D

---

### Post by Brhino on 2011-04-26
Hey.  I'm a few years late on this one but I got my old PS2 drums working with this on Ubuntu but there is a major delay   :(.  Does anyone know why this could be?

---

### Post by Perfect Storm on 2011-04-27
Thread closed - necromancing.
Try start a new thread or find a newer of date, thanks.


regards
A.I. Dude
Ubuntu Forum Staff

---


---
title: "Need help installing F-1 Spirit"
date: 2008-01-24
forum: Gaming &amp; Leisure
---

### Post by SpetsnazC4 on 2008-01-24
I am trying to install F-1 Spirit on Gutsy. It is a remake of a Konami racer.

[http://www.braingames.getput.com/f1spirit/download.html](http://www.braingames.getput.com/f1spirit/download.html)

I have unzipped it and in the sources folder there is a Makefile.

In the terminal I have navigated to the folder and tried Make.

I get this output:

> jared@jared-laptop:~/Desktop/F-1 Spirit/sources$ make
c++ -c -g3 -O3 state_gamestart.cpp -o state_gamestart.o `sdl-config --cflags` -I/usr/local/include/SDL
state_gamestart.cpp:13:23: error: SDL_mixer.h: No such file or directory
state_gamestart.cpp:14:21: error: SDL_net.h: No such file or directory
sound.h:4: error: expected initializer before ‘*’ token
sound.h:12: error: ‘SOUNDT’ does not name a type
sound.h:13: error: variable or field ‘Sound_delete_sound’ declared void
sound.h:13: error: ‘SOUNDT’ was not declared in this scope
sound.h:14: error: variable or field ‘Sound_play’ declared void
sound.h:14: error: ‘SOUNDT’ was not declared in this scope
sound.h:15: error: variable or field ‘Sound_play’ declared void
sound.h:15: error: redefinition of ‘int Sound_play’
sound.h:14: error: ‘int Sound_play’ previously defined here
sound.h:15: error: ‘SOUNDT’ was not declared in this scope
sound.h:15: error: expected primary-expression before ‘int’
sound.h:16: error: variable or field ‘Sound_play_ch’ declared void
sound.h:16: error: ‘SOUNDT’ was not declared in this scope
sound.h:16: error: expected primary-expression before ‘int’
sound.h:16: error: initializer expression list treated as compound expression
sound.h:17: error: variable or field ‘Sound_play_ch’ declared void
sound.h:17: error: redefinition of ‘int Sound_play_ch’
sound.h:16: error: ‘int Sound_play_ch’ previously defined here
sound.h:17: error: ‘SOUNDT’ was not declared in this scope
sound.h:17: error: expected primary-expression before ‘int’
sound.h:17: error: expected primary-expression before ‘int’
CCar.h:129: error: ‘SOUNDT’ has not been declared
CCar.h:129: error: ‘F1SpiritGame’ has not been declared
CCar.h:175: error: ‘CTrack’ has not been declared
CCar.h:205: error: ‘CTrack’ has not been declared
CCar.h:226: error: ISO C++ forbids declaration of ‘F1SpiritGame’ with no type
CCar.h:226: error: expected ‘;’ before ‘*’ token
CCar.h:275: error: ‘SOUNDT’ does not name a type
CCar.h:277: error: ‘Mix_Chunk’ does not name a type
ReplayInfo.h:53: error: ISO C++ forbids declaration of ‘F1SpiritGame’ with no type
ReplayInfo.h:53: error: expected ‘;’ before ‘*’ token
ReplayInfo.h:54: error: ‘F1SpiritGame’ has not been declared
F1SpiritGame.h:59: error: ‘SOUNDT’ has not been declared
F1SpiritGame.h:68: error: ‘SOUNDT’ does not name a type
F1SpiritGame.h:69: error: ‘SOUNDT’ does not name a type
F1SpiritGame.h:70: error: ‘SOUNDT’ does not name a type
F1SpiritGame.h:71: error: ‘SOUNDT’ does not name a type
F1SpiritGame.h:72: error: ‘SOUNDT’ does not name a type
F1SpiritGame.h:73: error: ‘SOUNDT’ does not name a type
F1SpiritApp.h:49: error: ‘IPaddress’ does not name a type
F1SpiritApp.h:50: error: ‘TCPsocket’ does not name a type
F1SpiritApp.h:51: error: ‘UDPsocket’ does not name a type
F1SpiritApp.h:125: error: ‘SOUNDT’ does not name a type
F1SpiritApp.h:228: error: ‘SOUNDT’ does not name a type
F1SpiritApp.h:241: error: ‘SDLNet_SocketSet’ does not name a type
make: *** [state_gamestart.o] Error 1


I am wondering if for some reason Ubuntu does not like the sysntax of the Makefile so I opened it up in a text editor. Here it is:

> OBJS := \
	2DCMC.o              RoadPiece.o         state_gamestart.o \
	CCar.o               SDL_glutaux.o       state_hiscore.o \
	CPlayer.o            Vector.o            state_konami.o \
	EnemyCCar.o          auxiliar.o          state_menu.o \
	F1Spirit-auxiliar.o               state_race.o \
	F1SpiritApp.o        geometrics.o        state_race_result.o \
	GLTile.o             keyboardstate.o     state_splash.o \
	GLtile-f1.o          main.o              state_title.o \
	PlacedGLTile.o       sound.o             state_trackload.o \
	PlayerCCar.o         track.o \
	RacingCCar.o         state_disclaimer.o  RotatedGLTile.o \
	debug.o			state_endsequence.o 	state_replaymanager.o \
	ReplayInfo.o		 F1SpiritGame.o		 ranrotb.o \
	GameParameters.o	 F1Shttp.o	F1SpiritTrackViewer.o \
	state_gameoptions.o F1SComputer.o state_menu_draw.o \
	state_menu_create_menu.o

all: f1s

%.o: %.cpp
	c++ -c -g3 -O3 $< -o $@ `sdl-config --cflags` -I/usr/local/include/SDL

# dynamically linked binary:
f1s: $(OBJS)
	c++ $^ -o $@ `sdl-config --libs` `curl-config --libs` -lSDL_net -lSDL_image -lSDL_mixer -lSDL_sound -lSDL_sound -lGL -lGLU -I/usr/local/include/SDL

clean:
	rm -f f1s
	rm -f *.o


I have no idea what could be out of place in it but I thought that I would include it.


I would appreciate any help. It looks like a pretty good racer and if this a common installation situation I would like to learn the process. I have installed from synaptic, apt-get, deb, rpm, and from source (all have had a ./configure file) but this is a new one for me. I haven't found a tutorial that would apply here.

Thanks.

---

### Post by harras on 2008-02-25
Install the following packages:
libsdl-dev
libsdl-mixer-dev
libsdl-net-dev

Usually U need the *-dev packages to compile something with dependencies.

---


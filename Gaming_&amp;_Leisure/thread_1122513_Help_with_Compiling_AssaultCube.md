---
title: "Help with Compiling AssaultCube"
date: 2009-04-11
forum: Gaming &amp; Leisure
---

### Post by MechWarrior001 on 2009-04-11
Hey, havn't been on the forums in awhile, anyways:

I recently found out about AssaultCube, thought I would give it a try.

I downloaded it, and Terminal said it didnt detect a prebuilt cube client, so, I followed the instructions to compile my own, and I seem to not be doing something right:

```
(Reading database ... 118011 files and directories currently installed.)
Preparing to replace libstdc++6 4.3.2-1ubuntu11 (using .../libstdc++6_4.3.2-1ubuntu12_i386.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.3.2-1ubuntu12) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 118011 files and directories currently installed.)
Preparing to replace libgomp1 4.3.2-1ubuntu11 (using .../libgomp1_4.3.2-1ubuntu12_i386.deb) ...
Unpacking replacement libgomp1 ...
Preparing to replace cpp-4.3 4.3.2-1ubuntu11 (using .../cpp-4.3_4.3.2-1ubuntu12_i386.deb) ...
Unpacking replacement cpp-4.3 ...
Preparing to replace gcc-4.3 4.3.2-1ubuntu11 (using .../gcc-4.3_4.3.2-1ubuntu12_i386.deb) ...
Unpacking replacement gcc-4.3 ...
Preparing to replace libgcc1 1:4.3.2-1ubuntu11 (using .../libgcc1_1%3a4.3.2-1ubuntu12_i386.deb) ...
Unpacking replacement libgcc1 ...
Processing triggers for man-db ...
Setting up libgcc1 (1:4.3.2-1ubuntu12) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libstdc++6-4.3-dev.
(Reading database ... 118011 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu12_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu12_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.3.1-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up libgomp1 (4.3.2-1ubuntu12) ...

Setting up cpp-4.3 (4.3.2-1ubuntu12) ...
Setting up gcc-4.3 (4.3.2-1ubuntu12) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu12) ...
Setting up g++-4.3 (4.3.2-1ubuntu12) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
philip@Philip-PC:~/Desktop/AssaultCube_v1.0.2/source/src$ make install
make -C ../enet all
make[1]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
Making all in include
make[2]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include'
make[3]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[3]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
Making all in enet
make[3]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include/enet'
make[4]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[4]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include/enet'
make[3]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include'
make[4]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[4]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include'
make[2]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include'
make[2]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[1]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o client.o client.cpp
In file included from client.cpp:3:
pch.h:42:23: error: SDL_image.h: No such file or directory
make: *** [client.o] Error 1
philip@Philip-PC:~/Desktop/AssaultCube_v1.0.2/source/src$ make install
make -C ../enet all
make[1]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
Making all in include
make[2]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include'
make[3]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[3]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
Making all in enet
make[3]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include/enet'
make[4]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[4]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include/enet'
make[3]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include'
make[4]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[4]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include'
make[2]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet/include'
make[2]: Entering directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
make[1]: Leaving directory `/home/philip/Desktop/AssaultCube_v1.0.2/source/enet'
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o client.o client.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o clientgame.o clientgame.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o clients2c.o clients2c.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o command.o command.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o console.o console.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o docs.o docs.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o editing.o editing.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o entities.o entities.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o log.o log.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o main.o main.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o menus.o menus.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o packetqueue.o packetqueue.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o physics.o physics.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o protocol.o protocol.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rendercubes.o rendercubes.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rendergl.o rendergl.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o renderhud.o renderhud.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rendermodel.o rendermodel.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o renderparticles.o renderparticles.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rendertext.o rendertext.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rndmap.o rndmap.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o scoreboard.o scoreboard.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o server.o server.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o serverbrowser.o serverbrowser.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o serverms.o serverms.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o shadow.o shadow.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o sound.o sound.cpp
sound.cpp:11:20: error: AL/al.h: No such file or directory
sound.cpp:12:21: error: AL/alc.h: No such file or directory
sound.cpp:13:31: error: vorbis/vorbisfile.h: No such file or directory
sound.cpp:26: error: expected constructor, destructor, or type conversion before ‘*’ token
sound.cpp:27: error: expected constructor, destructor, or type conversion before ‘*’ token
sound.cpp: In function ‘void alclearerr()’:
sound.cpp:33: error: ‘alGetError’ was not declared in this scope
sound.cpp: In function ‘bool alerr(bool, int)’:
sound.cpp:38: error: ‘ALenum’ was not declared in this scope
sound.cpp:38: error: expected `;' before ‘er’
sound.cpp:39: error: ‘er’ was not declared in this scope
sound.cpp:44: error: ‘AL_INVALID_NAME’ was not declared in this scope
sound.cpp:45: error: ‘AL_INVALID_ENUM’ was not declared in this scope
sound.cpp:46: error: ‘AL_INVALID_VALUE’ was not declared in this scope
sound.cpp:47: error: ‘AL_INVALID_OPERATION’ was not declared in this scope
sound.cpp:48: error: ‘AL_OUT_OF_MEMORY’ was not declared in this scope
sound.cpp:53: error: ‘er’ was not declared in this scope
sound.cpp: At global scope:
sound.cpp:71: error: ‘ALuint’ does not name a type
sound.cpp:156: error: ‘ALuint’ has not been declared
sound.cpp:174: error: ‘ALsizei’ has not been declared
sound.cpp:174: error: expected ‘,’ or ‘...’ before ‘*’ token
sound.cpp:174: error: ISO C++ forbids declaration of ‘ALuint’ with no type
sound.cpp: In constructor ‘source::source()’:
sound.cpp:77: error: class ‘source’ does not have any field named ‘id’
sound.cpp:80: error: ‘id’ was not declared in this scope
sound.cpp:80: error: ‘alIsSource’ was not declared in this scope
sound.cpp: In member function ‘void source::reset()’:
sound.cpp:100: error: ‘id’ was not declared in this scope
sound.cpp:100: error: ‘alIsSource’ was not declared in this scope
sound.cpp:119: error: ‘id’ was not declared in this scope
sound.cpp:119: error: ‘AL_REFERENCE_DISTANCE’ was not declared in this scope
sound.cpp:119: error: ‘alSourcef’ was not declared in this scope
sound.cpp:120: error: ‘AL_ROLLOFF_FACTOR’ was not declared in this scope
sound.cpp: In member function ‘bool source::generate()’:
sound.cpp:144: error: ‘id’ was not declared in this scope
sound.cpp:144: error: ‘alGenSources’ was not declared in this scope
sound.cpp: In member function ‘bool source::delete_()’:
sound.cpp:152: error: ‘id’ was not declared in this scope
sound.cpp:152: error: ‘alDeleteSources’ was not declared in this scope
sound.cpp: In member function ‘bool source::buffer(int)’:
sound.cpp:162: error: ‘id’ was not declared in this scope
sound.cpp:162: error: ‘AL_BUFFER’ was not declared in this scope
sound.cpp:162: error: ‘alSourcei’ was not declared in this scope
sound.cpp: In member function ‘bool source::looping(bool)’:
sound.cpp:170: error: ‘id’ was not declared in this scope
sound.cpp:170: error: ‘AL_LOOPING’ was not declared in this scope
sound.cpp:170: error: ‘alSourcei’ was not declared in this scope
sound.cpp: In member function ‘bool source::queuebuffers(int, int)’:
sound.cpp:177: error: ‘id’ was not declared in this scope
sound.cpp:177: error: ‘buffer_ids’ was not declared in this scope
sound.cpp:177: error: ‘alSourceQueueBuffers’ was not declared in this scope
sound.cpp: In member function ‘bool source::unqueueallbuffers()’:
sound.cpp:184: error: ‘ALint’ was not declared in this scope
sound.cpp:184: error: expected `;' before ‘queued’
sound.cpp:185: error: ‘id’ was not declared in this scope
sound.cpp:185: error: ‘AL_BUFFERS_QUEUED’ was not declared in this scope
sound.cpp:185: error: ‘queued’ was not declared in this scope
sound.cpp:185: error: ‘alGetSourcei’ was not declared in this scope
sound.cpp:189: error: ‘ALuint’ was not declared in this scope
sound.cpp:189: error: expected `;' before ‘buffer’
sound.cpp:190: error: ISO C++ forbids taking the address of an unqualified or parenthesized non-static member function to form a pointer to member function.  Say ‘&source::buffer’
sound.cpp:190: error: ‘alSourceUnqueueBuffers’ was not declared in this scope
sound.cpp: In member function ‘bool source::gain(float)’:
sound.cpp:198: error: ‘id’ was not declared in this scope
sound.cpp:198: error: ‘AL_GAIN’ was not declared in this scope
sound.cpp:198: error: ‘alSourcef’ was not declared in this scope
sound.cpp: In member function ‘bool source::pitch(float)’:
sound.cpp:205: error: ‘id’ was not declared in this scope
sound.cpp:205: error: ‘AL_PITCH’ was not declared in this scope
sound.cpp:205: error: ‘alSourcef’ was not declared in this scope
sound.cpp: In member function ‘bool source::position(const vec&)’:
sound.cpp:212: error: ‘id’ was not declared in this scope
sound.cpp:212: error: ‘AL_POSITION’ was not declared in this scope
sound.cpp:212: error: ‘ALfloat’ was not declared in this scope
sound.cpp:212: error: expected primary-expression before ‘)’ token
sound.cpp:212: error: ‘alSourcefv’ was not declared in this scope
sound.cpp: In member function ‘bool source::position(float, float, float)’:
sound.cpp:219: error: ‘id’ was not declared in this scope
sound.cpp:219: error: ‘AL_POSITION’ was not declared in this scope
sound.cpp:219: error: ‘alSource3f’ was not declared in this scope
sound.cpp: In member function ‘bool source::velocity(float, float, float)’:
sound.cpp:226: error: ‘id’ was not declared in this scope
sound.cpp:226: error: ‘AL_VELOCITY’ was not declared in this scope
sound.cpp:226: error: ‘alSource3f’ was not declared in this scope
sound.cpp: In member function ‘vec source::position()’:
sound.cpp:234: error: ‘id’ was not declared in this scope
sound.cpp:234: error: ‘AL_POSITION’ was not declared in this scope
sound.cpp:234: error: ‘ALfloat’ was not declared in this scope
sound.cpp:234: error: expected primary-expression before ‘)’ token
sound.cpp:234: error: ‘alGetSourcefv’ was not declared in this scope
sound.cpp: In member function ‘bool source::sourcerelative(bool)’:
sound.cpp:242: error: ‘id’ was not declared in this scope
sound.cpp:242: error: ‘AL_SOURCE_RELATIVE’ was not declared in this scope
sound.cpp:242: error: ‘AL_TRUE’ was not declared in this scope
sound.cpp:242: error: ‘AL_FALSE’ was not declared in this scope
sound.cpp:242: error: ‘alSourcei’ was not declared in this scope
sound.cpp: In member function ‘int source::state()’:
sound.cpp:248: error: ‘ALint’ was not declared in this scope
sound.cpp:248: error: expected `;' before ‘s’
sound.cpp:249: error: ‘id’ was not declared in this scope
sound.cpp:249: error: ‘AL_SOURCE_STATE’ was not declared in this scope
sound.cpp:249: error: ‘s’ was not declared in this scope
sound.cpp:249: error: ‘alGetSourcei’ was not declared in this scope
sound.cpp: In member function ‘bool source::secoffset(float)’:
sound.cpp:256: error: ‘id’ was not declared in this scope
sound.cpp:256: error: ‘AL_SEC_OFFSET’ was not declared in this scope
sound.cpp:256: error: ‘alSourcef’ was not declared in this scope
sound.cpp: In member function ‘float source::secoffset()’:
sound.cpp:265: error: ‘ALfloat’ was not declared in this scope
sound.cpp:265: error: expected `;' before ‘s’
sound.cpp:266: error: ‘id’ was not declared in this scope
sound.cpp:266: error: ‘AL_SEC_OFFSET’ was not declared in this scope
sound.cpp:266: error: ‘s’ was not declared in this scope
sound.cpp:266: error: ‘alGetSourcef’ was not declared in this scope
sound.cpp: In member function ‘bool source::playing()’:
sound.cpp:275: error: ‘AL_PLAYING’ was not declared in this scope
sound.cpp: In member function ‘bool source::play()’:
sound.cpp:281: error: ‘id’ was not declared in this scope
sound.cpp:281: error: ‘alSourcePlay’ was not declared in this scope
sound.cpp: In member function ‘bool source::stop()’:
sound.cpp:288: error: ‘id’ was not declared in this scope
sound.cpp:288: error: ‘alSourceStop’ was not declared in this scope
sound.cpp: In member function ‘bool source::rewind()’:
sound.cpp:295: error: ‘id’ was not declared in this scope
sound.cpp:295: error: ‘alSourceRewind’ was not declared in this scope
sound.cpp: In member function ‘void source::printposition()’:
sound.cpp:303: error: ‘ALint’ was not declared in this scope
sound.cpp:303: error: expected `;' before ‘s’
sound.cpp:304: error: ‘id’ was not declared in this scope
sound.cpp:304: error: ‘AL_SOURCE_TYPE’ was not declared in this scope
sound.cpp:304: error: ‘s’ was not declared in this scope
sound.cpp:304: error: ‘alGetSourcei’ was not declared in this scope
sound.cpp: At global scope:
sound.cpp:548: error: ‘ogg_int64_t’ has not been declared
sound.cpp:553: error: ‘ov_callbacks’ does not name a type
sound.cpp:569: error: ‘OggVorbis_File’ does not name a type
sound.cpp:571: error: ISO C++ forbids declaration of ‘vorbis_info’ with no type
sound.cpp:571: error: expected ‘;’ before ‘*’ token
sound.cpp:576: error: ‘ALuint’ does not name a type
sound.cpp:578: error: ‘ALenum’ does not name a type
sound.cpp:696: error: ‘ALuint’ has not been declared
sound.cpp: In constructor ‘oggstream::oggstream()’:
sound.cpp:608: error: ‘bufferids’ was not declared in this scope
sound.cpp:608: error: ‘alGenBuffers’ was not declared in this scope
sound.cpp: In destructor ‘virtual oggstream::~oggstream()’:
sound.cpp:618: error: ‘bufferids’ was not declared in this scope
sound.cpp:618: error: ‘alIsBuffer’ was not declared in this scope
sound.cpp:621: error: ‘alDeleteBuffers’ was not declared in this scope
sound.cpp: In member function ‘void oggstream::reset()’:
sound.cpp:637: error: ‘format’ was not declared in this scope
sound.cpp:637: error: ‘AL_NONE’ was not declared in this scope
sound.cpp:642: error: ‘oggfile’ was not declared in this scope
sound.cpp:642: error: ‘ov_clear’ was not declared in this scope
sound.cpp:644: error: ‘info’ was not declared in this scope
sound.cpp: In member function ‘bool oggstream::open(const char*)’:
sound.cpp:668: error: ‘oggfile’ was not declared in this scope
sound.cpp:668: error: ‘oggcallbacks’ was not declared in this scope
sound.cpp:668: error: ‘ov_open_callbacks’ was not declared in this scope
sound.cpp:675: error: ‘info’ was not declared in this scope
sound.cpp:675: error: ‘ov_info’ was not declared in this scope
sound.cpp:676: error: ‘format’ was not declared in this scope
sound.cpp:676: error: ‘AL_FORMAT_STEREO16’ was not declared in this scope
sound.cpp:676: error: ‘AL_FORMAT_MONO16’ was not declared in this scope
sound.cpp:677: error: ‘ov_time_total’ was not declared in this scope
sound.cpp: In member function ‘bool oggstream::stream(int)’:
sound.cpp:703: error: ‘ALsizei’ was not declared in this scope
sound.cpp:703: error: expected `;' before ‘size’
sound.cpp:705: error: ‘size’ was not declared in this scope
sound.cpp:707: error: ‘oggfile’ was not declared in this scope
sound.cpp:707: error: ‘ov_read’ was not declared in this scope
sound.cpp:713: error: ‘size’ was not declared in this scope
sound.cpp:715: error: ‘oggfile’ was not declared in this scope
sound.cpp:715: error: ‘ov_pcm_seek’ was not declared in this scope
sound.cpp:720: error: ‘format’ was not declared in this scope
sound.cpp:720: error: ‘size’ was not declared in this scope
sound.cpp:720: error: ‘info’ was not declared in this scope
sound.cpp:720: error: ‘alBufferData’ was not declared in this scope
sound.cpp: In member function ‘bool oggstream::update()’:
sound.cpp:733: error: ‘ALint’ was not declared in this scope
sound.cpp:733: error: expected `;' before ‘processed’
sound.cpp:735: error: ‘struct source’ has no member named ‘id’
sound.cpp:735: error: ‘AL_BUFFERS_PROCESSED’ was not declared in this scope
sound.cpp:735: error: ‘processed’ was not declared in this scope
sound.cpp:735: error: ‘alGetSourcei’ was not declared in this scope
sound.cpp:738: error: ‘ALuint’ was not declared in this scope
sound.cpp:738: error: expected `;' before ‘buffer’
sound.cpp:739: error: ‘struct source’ has no member named ‘id’
sound.cpp:739: error: ‘buffer’ was not declared in this scope
sound.cpp:739: error: ‘alSourceUnqueueBuffers’ was not declared in this scope
sound.cpp:741: error: ‘struct source’ has no member named ‘id’
sound.cpp:741: error: ‘alSourceQueueBuffers’ was not declared in this scope
sound.cpp: In member function ‘bool oggstream::playback(bool)’:
sound.cpp:826: error: ‘bufferids’ was not declared in this scope
sound.cpp:830: error: ‘bufferids’ was not declared in this scope
sound.cpp: In member function ‘void oggstream::seek(double)’:
sound.cpp:840: error: ‘oggfile’ was not declared in this scope
sound.cpp:840: error: ‘ov_time_seek_page’ was not declared in this scope
sound.cpp: At global scope:
sound.cpp:846: error: ‘ALuint’ does not name a type
sound.cpp: In constructor ‘sbuffer::sbuffer()’:
sound.cpp:849: error: class ‘sbuffer’ does not have any field named ‘id’
sound.cpp: In member function ‘bool sbuffer::load()’:
sound.cpp:861: error: ‘id’ was not declared in this scope
sound.cpp:863: error: ‘id’ was not declared in this scope
sound.cpp:863: error: ‘alGenBuffers’ was not declared in this scope
sound.cpp:879: error: ‘OggVorbis_File’ was not declared in this scope
sound.cpp:879: error: expected `;' before ‘oggfile’
sound.cpp:880: error: ‘oggfile’ was not declared in this scope
sound.cpp:880: error: ‘oggcallbacks’ was not declared in this scope
sound.cpp:880: error: ‘ov_open_callbacks’ was not declared in this scope
sound.cpp:882: error: ‘vorbis_info’ was not declared in this scope
sound.cpp:882: error: ‘info’ was not declared in this scope
sound.cpp:882: error: ‘ov_info’ was not declared in this scope
sound.cpp:892: error: ‘ov_read’ was not declared in this scope
sound.cpp:896: error: ‘AL_FORMAT_STEREO16’ was not declared in this scope
sound.cpp:896: error: ‘AL_FORMAT_MONO16’ was not declared in this scope
sound.cpp:896: error: ‘alBufferData’ was not declared in this scope
sound.cpp:897: error: ‘ov_clear’ was not declared in this scope
sound.cpp:917: error: ‘ALenum’ was not declared in this scope
sound.cpp:917: error: expected `;' before ‘format’
sound.cpp:922: error: ‘format’ was not declared in this scope
sound.cpp:922: error: ‘AL_FORMAT_STEREO8’ was not declared in this scope
sound.cpp:922: error: ‘AL_FORMAT_MONO8’ was not declared in this scope
sound.cpp:926: error: ‘AL_FORMAT_STEREO16’ was not declared in this scope
sound.cpp:926: error: ‘AL_FORMAT_MONO16’ was not declared in this scope
sound.cpp:934: error: ‘format’ was not declared in this scope
sound.cpp:934: error: ‘alBufferData’ was not declared in this scope
sound.cpp: In member function ‘void sbuffer::unload()’:
sound.cpp:949: error: ‘id’ was not declared in this scope
sound.cpp:951: error: ‘id’ was not declared in this scope
sound.cpp:951: error: ‘alIsBuffer’ was not declared in this scope
sound.cpp:951: error: ‘alDeleteBuffers’ was not declared in this scope
sound.cpp:952: error: ‘id’ was not declared in this scope
sound.cpp: In constructor ‘location::location(int, const worldobjreference&, int)’:
sound.cpp:1026: error: ‘struct sbuffer’ has no member named ‘id’
sound.cpp:1035: error: ‘struct sbuffer’ has no member named ‘id’
sound.cpp: In member function ‘void location::update()’:
sound.cpp:1162: error: ‘AL_PLAYING’ was not declared in this scope
sound.cpp:1165: error: ‘AL_STOPPED’ was not declared in this scope
sound.cpp:1166: error: ‘AL_PAUSED’ was not declared in this scope
sound.cpp:1167: error: ‘AL_INITIAL’ was not declared in this scope
sound.cpp: In function ‘void var_soundvol()’:
sound.cpp:1326: error: ‘AL_GAIN’ was not declared in this scope
sound.cpp:1326: error: ‘alListenerf’ was not declared in this scope
sound.cpp: In function ‘void initsound()’:
sound.cpp:1356: error: ‘device’ was not declared in this scope
sound.cpp:1357: error: ‘context’ was not declared in this scope
sound.cpp:1360: error: ‘alcIsExtensionPresent’ was not declared in this scope
sound.cpp:1362: error: expected initializer before ‘*’ token
sound.cpp:1363: error: ‘devices’ was not declared in this scope
sound.cpp:1369: error: expected initializer before ‘*’ token
sound.cpp:1369: error: ‘c’ was not declared in this scope
sound.cpp:1380: error: ‘alcOpenDevice’ was not declared in this scope
sound.cpp:1384: error: ‘alcCreateContext’ was not declared in this scope
sound.cpp:1387: error: ‘alcMakeContextCurrent’ was not declared in this scope
sound.cpp:1389: error: ‘AL_INVERSE_DISTANCE_CLAMPED’ was not declared in this scope
sound.cpp:1389: error: ‘alDistanceModel’ was not declared in this scope
sound.cpp:1392: error: ‘ALC_DEVICE_SPECIFIER’ was not declared in this scope
sound.cpp:1392: error: ‘alcGetString’ was not declared in this scope
sound.cpp:1392: error: ‘AL_RENDERER’ was not declared in this scope
sound.cpp:1392: error: ‘alGetString’ was not declared in this scope
sound.cpp:1392: error: ‘AL_VENDOR’ was not declared in this scope
sound.cpp:1393: error: ‘AL_VERSION’ was not declared in this scope
sound.cpp:1410: error: ‘alcDestroyContext’ was not declared in this scope
sound.cpp:1411: error: ‘alcCloseDevice’ was not declared in this scope
sound.cpp: In function ‘void soundcleanup()’:
sound.cpp:1564: error: ‘alcMakeContextCurrent’ was not declared in this scope
sound.cpp:1565: error: ‘context’ was not declared in this scope
sound.cpp:1565: error: ‘alcDestroyContext’ was not declared in this scope
sound.cpp:1566: error: ‘device’ was not declared in this scope
sound.cpp:1566: error: ‘alcCloseDevice’ was not declared in this scope
sound.cpp: In function ‘void updateaudio()’:
sound.cpp:1670: error: ‘context’ was not declared in this scope
sound.cpp:1670: error: ‘alcSuspendContext’ was not declared in this scope
sound.cpp:1762: error: ‘AL_ORIENTATION’ was not declared in this scope
sound.cpp:1762: error: ‘ALfloat’ was not declared in this scope
sound.cpp:1762: error: expected primary-expression before ‘)’ token
sound.cpp:1762: error: ‘alListenerfv’ was not declared in this scope
sound.cpp:1763: error: ‘AL_POSITION’ was not declared in this scope
sound.cpp:1763: error: expected primary-expression before ‘)’ token
sound.cpp:1765: error: ‘alcProcessContext’ was not declared in this scope
sound.cpp: At global scope:
sound.cpp:548: warning: ‘int oggseek(FILE*, int, int)’ defined but not used
sound.cpp:1484: warning: ‘__dummy_registermusic’ defined but not used
sound.cpp:1485: warning: ‘__dummy_music’ defined but not used
sound.cpp:1515: warning: ‘__dummy_registersound’ defined but not used
sound.cpp:1518: warning: ‘__dummy_mapsound’ defined but not used
sound.cpp:1545: warning: ‘__dummy_applymapsoundchanges’ defined but not used
sound.cpp:1583: warning: ‘__dummy_mapsoundreset’ defined but not used
sound.cpp:1790: warning: ‘__dummy_unmuteallsounds’ defined but not used
sound.cpp:1791: warning: ‘__dummy_mutesound’ defined but not used
sound.cpp:1792: warning: ‘__dummy_soundmuted’ defined but not used
sound.cpp:1849: warning: ‘__dummy_sound’ defined but not used
sound.cpp:1886: warning: ‘__dummy_voicecom’ defined but not used
sound.cpp:1900: warning: ‘__dummy_soundtest’ defined but not used
make: *** [sound.o] Error 1
philip@Philip-PC:~/Desktop/AssaultCube_v1.0.2/source/src$ '/home/philip/Desktop/AssaultCube_v1.0.2/assaultcube.sh' 
Your platform does not have a pre-compiled Cube client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, OpenAL, and OpenGL libraries installed.
2) Change directory to source/src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.
philip@Philip-PC:~/Desktop/AssaultCube_v1.0.2/source/src$ 

```

Originally I had a problem becuase it couldnt find *SDL_Image.h*, so I copied it from *source/include* to *source/src*, and thats when I got this problem.

Does anyone know how to fix it?

P.S. I'm using a Creative X-Fi Fatal1ty card with Creative's (Beta, in my opinion) 32-Bit/x86 Linux Driver (Compiled install, no .deb)

---

### Post by xtremethegreat1 on 2009-04-11
It looks like you have not yet installed dependencies. Dependencies are programs or libraries that are needed to compile something that depends on it. From the code you have given above, I can figure out, that you need to install the dependencies I'm pointing out below.

The dependencies:

libvorbia0a
libvorbis-dev
libvorbisenc2
libvorbisfile3
libopenal-dev
libopenal1
libsdl1.2debian
libsdl1.2-dev
libsdl-image1.2
libsdl-image1.2-dev
libgl1-mesa-dev

To install all these, just enter the following command in the command line:

```
sudo apt-get install libvorbia0a libvorbis-dev libvorbisenc2 libvorbisfile3 libopenal-dev libopenal1 libsdl1.2debian libsdl1.2-dev libsdl-image1.2 libsdl-image1.2-dev libgl1-mesa-dev
```

The last one, I'm not very sure. But OpenGL libraries should be already installed. Try this. I hope it works.

:lolflag:

---

### Post by xtremethegreat1 on 2009-04-11
Also check the System Setting checkbox.

---

### Post by xtremethegreat1 on 2009-04-11
Oops the last reply was meant for a different post. Consider the first reply...

---

### Post by MechWarrior001 on 2009-04-11
Thanks man, Anyways, I have another problem:

```
stacktrace:
/home/philip/AssaultCube_v1.0.2/ac_client(_ZN12signalbinder11stackdumperEi+0x26) [0x81094d6]
[0xb803c400]
[0xb803c430]
/lib/tls/i686/cmov/libc.so.6(gsignal+0x50) [0xb791e880]
/lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb7920248]
/usr/lib/libGLcore.so.1 [0xb7171385]
AssaultCube error (6) ()
OpenAL Error (A004): invalid operation, line 953
OpenAL Error (A004): invalid operation, line 953
AL lib: ALc.c:1253: exit() 1 device(s) and 1 context(s) NOT deleted
AL lib: alSource.c:2291: alcDestroyContext(): 32 Source(s) NOT deleted
AL lib: alBuffer.c:1097: exit() 4 Buffer(s) NOT deleted

```

I'm not sure what to do, every time I launch it, the screen goes black for a few seconds, then I see the mouse pointer for 1-2 seconds and it crashes back to the desktop.

I wonder if its because I'm using a creative card.

---


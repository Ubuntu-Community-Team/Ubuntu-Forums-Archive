---
title: "error when install supertuxkart game ?"
date: 2006-10-13
forum: Gaming &amp; Leisure
---

### Post by ghostshadow189 on 2006-10-13
hi all, 
i'm trying to install supertuxkart , it's a racing game , and i've these error when make (after configure successfully) . so how can i fix this

```
In file included from sdldrv.cxx:28:
Driver.h:23:22: error: plib/ssg.h: No such file or directory
Driver.h:24:21: error: plib/sg.h: No such file or directory
Driver.h:103: error: ‘sgCoord’ does not name a type
Driver.h:107: error: ‘sgCoord’ does not name a type
Driver.h:109: error: ‘sgCoord’ does not name a type
Driver.h:110: error: ‘sgCoord’ does not name a type
Driver.h:112: error: ‘sgCoord’ does not name a type
Driver.h:113: error: ‘sgCoord’ does not name a type
Driver.h:117: error: ‘sgVec3’ does not name a type
Driver.h:125: error: ISO C++ forbids declaration of ‘ssgBranch’ with no type
Driver.h:125: error: expected ‘;’ before ‘*’ token
Driver.h:127: error: ISO C++ forbids declaration of ‘ssgTransform’ with no type
Driver.h:127: error: expected ‘;’ before ‘*’ token
Driver.h:130: error: ISO C++ forbids declaration of ‘ssgTransform’ with no type
Driver.h:130: error: expected ‘;’ before ‘*’ token
Driver.h:146: error: ‘sgVec3’ does not name a type
Driver.h:147: error: ‘sgVec3’ does not name a type
Driver.h:150: error: ‘sgVec3’ has not been declared
Driver.h:150: error: ‘sgVec3’ has not been declared
Driver.h:151: error: ‘sgVec3’ has not been declared
Driver.h:151: error: ‘sgVec3’ has not been declared
Driver.h:154: error: ‘sgVec2’ does not name a type
Driver.h:155: error: ‘sgVec2’ does not name a type
Driver.h:180: error: ‘sgCoord’ has not been declared
Driver.h:185: error: ISO C++ forbids declaration of ‘ssgBranch’ with no type
Driver.h:185: error: expected ‘;’ before ‘*’ token
Driver.h:187: error: expected `;' before ‘ssgEntity’
Driver.h:195: error: ISO C++ forbids declaration of ‘sgCoord’ with no type
Driver.h:195: error: expected ‘;’ before ‘*’ token
Driver.h:200: error: expected `;' before ‘void’
Driver.h:200: error: ‘sgCoord’ has not been declared
Driver.h:205: error: ISO C++ forbids declaration of ‘sgCoord’ with no type
Driver.h:205: error: expected ‘;’ before ‘*’ token
Driver.h:210: error: expected `;' before ‘sgCoord’
Driver.h:210: error: ISO C++ forbids declaration of ‘sgCoord’ with no type
Driver.h:210: error: expected ‘;’ before ‘*’ token
Driver.h:215: error: expected `;' before ‘void’
Driver.h:215: error: ‘sgCoord’ has not been declared
Driver.h: In member function ‘float Driver::getDistanceDownTrack()’:
Driver.h:169: error: ‘curr_track_coords’ was not declared in this scope
Driver.h: In member function ‘void Driver::setReset(int*)’:
Driver.h:182: error: ‘reset_pos’ was not declared in this scope
Driver.h:182: error: ‘sgCopyCoord’ was not declared in this scope
Driver.h: In member function ‘ssgEntity* Driver::getRoot()’:
Driver.h:188: error: ‘comp_model’ was not declared in this scope
Driver.h: In member function ‘void Driver::setVelocity(int*)’:
Driver.h:202: error: ‘velocity’ was not declared in this scope
Driver.h:202: error: ‘sgCopyCoord’ was not declared in this scope
Driver.h: In member function ‘void Driver::setCoord(int*)’:
Driver.h:217: error: ‘position’ was not declared in this scope
Driver.h:217: error: ‘sgCopyCoord’ was not declared in this scope
ParticleSystem.h: At global scope:
ParticleSystem.h:27: error: ‘sgVec4’ does not name a type
ParticleSystem.h:28: error: ‘sgVec3’ does not name a type
ParticleSystem.h:29: error: ‘sgVec3’ does not name a type
ParticleSystem.h:30: error: ‘sgVec3’ does not name a type
ParticleSystem.h: In member function ‘void Particle::update(float)’:
ParticleSystem.h:39: error: ‘vel’ was not declared in this scope
ParticleSystem.h:39: error: ‘acc’ was not declared in this scope
ParticleSystem.h:39: error: ‘sgAddScaledVec3’ was not declared in this scope
ParticleSystem.h:40: error: ‘pos’ was not declared in this scope
ParticleSystem.h: In constructor ‘Particle::Particle()’:
ParticleSystem.h:46: error: ‘col’ was not declared in this scope
ParticleSystem.h:46: error: ‘sgSetVec4’ was not declared in this scope
ParticleSystem.h:47: error: ‘pos’ was not declared in this scope
ParticleSystem.h:47: error: ‘sgZeroVec3’ was not declared in this scope
ParticleSystem.h:48: error: ‘vel’ was not declared in this scope
ParticleSystem.h:49: error: ‘acc’ was not declared in this scope
ParticleSystem.h: At global scope:
ParticleSystem.h:61: error: expected class-name before ‘{’ token
World.h:42: error: ISO C++ forbids declaration of ‘ssgRoot’ with no type
World.h:42: error: expected ‘;’ before ‘*’ token
World.h:90: error: ISO C++ forbids declaration of ‘ssgBranch’ with no type
World.h:90: error: expected ‘;’ before ‘*’ token
KartDriver.h:63: error: ISO C++ forbids declaration of ‘ssgSelector’ with no type
KartDriver.h:63: error: expected ‘;’ before ‘*’ token
KartDriver.h:65: error: ISO C++ forbids declaration of ‘ssgSimpleState’ with no type
KartDriver.h:65: error: expected ‘;’ before ‘*’ token
KartDriver.h:68: error: ISO C++ forbids declaration of ‘ssgTransform’ with no type
KartDriver.h:68: error: expected ‘;’ before ‘*’ token
KartDriver.h:72: error: ISO C++ forbids declaration of ‘ssgTransform’ with no type
KartDriver.h:72: error: expected ‘;’ before ‘*’ token
KartDriver.h:73: error: ISO C++ forbids declaration of ‘ssgTransform’ with no type
KartDriver.h:73: error: expected ‘;’ before ‘*’ token
KartDriver.h:74: error: ISO C++ forbids declaration of ‘ssgTransform’ with no type
KartDriver.h:74: error: expected ‘;’ before ‘*’ token
KartDriver.h:75: error: ISO C++ forbids declaration of ‘ssgTransform’ with no type
KartDriver.h:75: error: expected ‘;’ before ‘*’ token
KartDriver.h:82: error: ‘ssgBranch’ has not been declared
KartDriver.h: In member function ‘void KartDriver::addAttachment(ssgEntity*)’:
KartDriver.h:100: error: ‘attachment’ was not declared in this scope
KartDriver.h:102: error: expected type-specifier before ‘ssgSelector’
KartDriver.h:102: error: expected `;' before ‘ssgSelector’
KartDriver.h:103: error: ‘getModel’ was not declared in this scope
KartDriver.h:106: error: ‘attachment’ was not declared in this scope
KartDriver.h: In member function ‘void KartDriver::attach(int, float)’:
KartDriver.h:112: error: ‘attachment’ was not declared in this scope
KartDriver.h: At global scope:
KartDriver.h:142: error: ‘sgVec3’ has not been declared
KartDriver.h: In constructor ‘TrafficDriver::TrafficDriver(World*, const KartProperties*, int)’:
KartDriver.h:145: error: ‘reset_pos’ was not declared in this scope
KartDriver.h:145: error: ‘sgCopyVec3’ was not declared in this scope
Controller.h: At global scope:
Controller.h:29: warning: ‘class Controller’ has virtual functions but non-virtual destructor
PlayerDriver.h:38: warning: ‘class PlayerDriver’ has virtual functions but non-virtual destructor
make[1]: *** [sdldrv.o] Error 1
make[1]: Leaving directory `/home/ktsm/Downloads/games/supertuxkart-0.0.0-1/src'make: *** [all-recursive] Error 1

```

thanx for all ur helps

---


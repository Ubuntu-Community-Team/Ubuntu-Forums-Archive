---
title: "Programming Lego Mindstorms NXT with NXC (not exaclty C)"
date: 2013-03-12
forum: Gaming &amp; Leisure
---

### Post by schwarzer ritter on 2013-03-12
Hello, I'm currently trying to program a Lego Mindstorms NXT brick via the NXC programming language. To do so, I have downloaded the NXC compiler and moved it to /usr/local/bin and set up the usb connection (according to [http://www.eggwall.com/2011/07/setting-up-lego-programming-environment.html](http://www.eggwall.com/2011/07/setting-up-lego-programming-environment.html) and [http://bricxcc.sourceforge.net/nbc/doc/nxtlinux.txt](http://bricxcc.sourceforge.net/nbc/doc/nxtlinux.txt)).
When I compile a program (file ending .nxc), it suceeds, but maybe it even downloads it to the NXT, but I can't see it in the program files menu on the brick.
Here is my output: ```
user@mymachine:~/path/to/directory$ nbc sample.nxc -d -S=usb
# Status: Current file = "/home/manuel/Dokumente/mindstorms/sample.nxc"
# Status: NXC compilation begins
# Status: Compiling for firmware version 128, NBC/NXC enhanced = FALSE
# Status: Running NXC preprocessor
# Status: Include path = /home/manuel/Dokumente/mindstorms/;/usr/local/bin/;/usr/local/include/nbc/
# Status: Processing include: NBCCommon.h
# Status: NXC init program
# Status: Current file = "NXCDefs.h"
# Status: NXC parse program code
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorType
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorMode
# Status: NXC processing global declarations
# Status: NXC processing procedure block: ClearSensor
# Status: NXC processing global declarations
# Status: NXC processing procedure block: ResetSensor
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensor
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorTouch
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorLight
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorSound
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorLowspeed
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorUltrasonic
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorEMeter
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorTemperature
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorColorFull
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorColorRed
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorColorGreen
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorColorBlue
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorColorNone
# Status: NXC processing global declarations
# Status: NXC processing procedure block: ClearScreen
# Status: NXC processing global declarations
# Status: NXC processing procedure block: ClearLine
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetDisplayFont
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetDisplayDisplay
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetDisplayEraseMask
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetDisplayFlags
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetDisplayTextLinesCenterFlags
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetDisplayUpdateMask
# Status: NXC processing global declarations
# Status: NXC processing procedure block: PlaySound
# Status: NXC processing global declarations
# Status: NXC processing procedure block: PlayTones
# Status: NXC processing global declarations
# Status: NXC processing procedure block: Wait
# Status: NXC processing global declarations
# Status: NXC processing procedure block: Yield
# Status: NXC processing global declarations
# Status: NXC processing procedure block: StopAllTasks
# Status: NXC processing global declarations
# Status: NXC processing procedure block: PowerDown
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SleepNow
# Status: NXC processing global declarations
# Status: NXC processing procedure block: RebootInFirmwareMode
# Status: NXC processing global declarations
# Status: NXC processing function block: SensorHTGyro
# Status: NXC processing function block: SensorHTMagnet
# Status: NXC processing function block: SensorHTEOPD
# Status: NXC processing procedure block: SetSensorHTEOPD
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorHTGyro
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorHTMagnet
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorMSPressure
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorMSDROD
# Status: NXC processing global declarations
# Status: NXC processing procedure block: SetSensorNXTSumoEyes
# Status: NXC processing global declarations
# Status: NXC processing function block: SensorMSPressure
# Status: NXC processing function block: SensorNXTSumoEyes
# Status: NXC processing function block: sqrt
# Status: NXC processing function block: bcd2dec
# Status: NXC processing function block: fclose
# Status: NXC processing function block: remove
# Status: NXC processing function block: rename
# Status: NXC processing function block: fgetc
# Status: NXC processing function block: fgets
# Status: NXC processing function block: feof
# Status: NXC processing procedure block: set_fopen_size
# Status: NXC processing global declarations
# Status: NXC processing function block: fopen
# Status: NXC processing function block: fflush
# Status: NXC processing function block: fputc
# Status: NXC processing function block: fputs
# Status: NXC processing function block: atoi
# Status: NXC processing function block: atol
# Status: NXC processing function block: labs
# Status: NXC processing function block: atof
# Status: NXC processing function block: strtod
# Status: NXC processing function block: strtol
# Status: NXC processing function block: strtoul
# Status: NXC processing function block: div
# Status: NXC processing function block: ldiv
# Status: NXC processing function block: Pos
# Status: NXC processing function block: ByteArrayToStr
# Status: NXC processing procedure block: ByteArrayToStrEx
# Status: NXC processing global declarations
# Status: NXC processing procedure block: StrToByteArray
# Status: NXC processing global declarations
# Status: NXC processing function block: Copy
# Status: NXC processing function block: MidStr
# Status: NXC processing function block: RightStr
# Status: NXC processing function block: LeftStr
# Status: NXC processing function block: strlen
# Status: NXC processing function block: strcat
# Status: NXC processing function block: strncat
# Status: NXC processing function block: strcpy
# Status: NXC processing function block: strncpy
# Status: NXC processing function block: strcmp
# Status: NXC processing function block: strncmp
# Status: NXC processing function block: isupper
# Status: NXC processing function block: islower
# Status: NXC processing function block: isalpha
# Status: NXC processing function block: isdigit
# Status: NXC processing function block: isalnum
# Status: NXC processing function block: isspace
# Status: NXC processing function block: iscntrl
# Status: NXC processing function block: isprint
# Status: NXC processing function block: isgraph
# Status: NXC processing function block: ispunct
# Status: NXC processing function block: isxdigit
# Status: NXC processing function block: toupper
# Status: NXC processing function block: tolower
# Status: NXC processing procedure block: glInit
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glSet
# Status: NXC processing global declarations
# Status: NXC processing function block: glBeginObject
# Status: NXC processing procedure block: glEndObject
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glObjectAction
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glAddVertex
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glBegin
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glEnd
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glBeginRender
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glCallObject
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glFinishRender
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glSetAngleX
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glAddToAngleX
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glSetAngleY
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glAddToAngleY
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glSetAngleZ
# Status: NXC processing global declarations
# Status: NXC processing procedure block: glAddToAngleZ
# Status: NXC processing global declarations
# Status: NXC processing function block: glSin32768
# Status: NXC processing function block: glCos32768
# Status: NXC processing function block: glBox
# Status: NXC processing function block: glCube
# Status: NXC processing function block: glPyramid
# Status: Current file = "/home/manuel/Dokumente/mindstorms/sample.nxc"
# Status: NXC processing procedure block: main
# Status: NXC processing global declarations
# Status: NXC generate trailer
# Status: NXC code generation finished
# Status: NBC compilation begins
# Status: Compiling for firmware version 128, NBC/NXC enhanced = FALSE
# Status: Loading NBC system files
# Status: Running NBC Preprocessor
# Status: Include path = /home/manuel/Dokumente/mindstorms/;/usr/local/bin/;/usr/local/include/nbc/
# Status: Processing include: NBCCommon.h
# Status: Compiling NBC source code
# Status: Finished compiling NBC source code
# Status: Finalizing dependencies
# Status: Optimizing at level 1
# Status: Build codespace references
# Status: Optimize mutexes
# Status: Compact the codespace
# Status: Remove unused labels
# Status: Compact the dataspace
# Status: Sort the dataspace
# Status: Generate raw dataspace data
# Status: Fill clump and codespace arrays
# Status: Update executable file header
# Status: Write file header to executable
# Status: Write dataspace to executable
# Status: Write clump data to executable
# Status: Write code to executable
# Status: Write optimized source to compiler output
# Status: Finished
# Status: Firmware version check failed.


```

---


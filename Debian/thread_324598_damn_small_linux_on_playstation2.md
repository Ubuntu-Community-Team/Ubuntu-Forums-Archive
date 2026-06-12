---
title: "damn small linux on playstation2"
date: 2006-12-24
forum: Debian
---

### Post by dbbolton on 2006-12-24
is it possible ?

---

### Post by dbbolton on 2006-12-24
[quote=wikipedia]
**Technical specifications**

 The specifications of the PlayStation 2 console are as follows, with hardware revisions:
  [[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Sony_EmotionEngine_CXD9615GB_top.jpg/180px-Sony_EmotionEngine_CXD9615GB_top.jpg[/IMG]]("http://en.wikipedia.org/wiki/Image:Sony_EmotionEngine_CXD9615GB_top.jpg")  [[IMG]http://en.wikipedia.org/skins-1.5/common/images/magnify-clip.png[/IMG]]("http://en.wikipedia.org/wiki/Image:Sony_EmotionEngine_CXD9615GB_top.jpg")
 [Emotion Engine]("http://en.wikipedia.org/wiki/Emotion_Engine") CPU
 
 
  [[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Sony_Graphics_Synthesizer_CXD29314GB.jpg/180px-Sony_Graphics_Synthesizer_CXD29314GB.jpg[/IMG]]("http://en.wikipedia.org/wiki/Image:Sony_Graphics_Synthesizer_CXD29314GB.jpg")  [[IMG]http://en.wikipedia.org/skins-1.5/common/images/magnify-clip.png[/IMG]]("http://en.wikipedia.org/wiki/Image:Sony_Graphics_Synthesizer_CXD29314GB.jpg")
 [Graphics Synthesizer]("http://en.wikipedia.org/wiki/Graphics_Synthesizer") GPU
 
 
  [[IMG]http://upload.wikimedia.org/wikipedia/commons/5/57/Sony_Playstation_1_CPU.jpg[/IMG]]("http://en.wikipedia.org/wiki/Image:Sony_Playstation_1_CPU.jpg")  [[IMG]http://en.wikipedia.org/skins-1.5/common/images/magnify-clip.png[/IMG]]("http://en.wikipedia.org/wiki/Image:Sony_Playstation_1_CPU.jpg")
 [I/O Processor (PlayStation 1 CPU)]("http://en.wikipedia.org/wiki/I/O_Processor_%28PlayStation_1_CPU%29") I/O Bus
 
 
 [LIST]
[*][CPU]("http://en.wikipedia.org/wiki/Central_processing_unit"): 128 bit "[Emotion Engine]("http://en.wikipedia.org/wiki/Emotion_Engine")" clocked at 294 MHz, 10.5 million transistors[LIST]
[*][System Memory]("http://en.wikipedia.org/wiki/Main_memory"): 32 MB Direct [Rambus]("http://en.wikipedia.org/wiki/Rambus") or [RDRAM]("http://en.wikipedia.org/wiki/RDRAM") (note that some computers use this type of [RAM]("http://en.wikipedia.org/wiki/RAM"))
[*][Memory bus]("http://en.wikipedia.org/wiki/Memory_bus") Bandwidth: 3.2 GB per second
[*]Main processor: [MIPS]("http://en.wikipedia.org/wiki/MIPS_architecture") R5900 CPU core, 64 bit
[*][Coprocessor]("http://en.wikipedia.org/wiki/Coprocessor"): [FPU]("http://en.wikipedia.org/wiki/Floating_Point_Unit") (Floating Point Multiply Accumulator × 1, Floating Point Divider × 1)
[*]Vector Units: VU0 and VU1 (Floating Point Multiply Accumulator × 9, Floating Point Divider × 1), 128 bit, vu0 used for physics and other gameplay type things, vu1 used for polygon transformations and other visual based calculation
[*]Floating Point Performance: 6.2 GFLOPS (single precision 32-bit floating point), about 2.9 on each vector unit
[*]3D CG Geometric Transformation: 66 million polygons per second[[15]]("http://en.wikipedia.org/wiki/PlayStation_2#_note-10")
[*]Compressed Image Decoder: [MPEG-2]("http://en.wikipedia.org/wiki/MPEG-2")
[*]I/O Processor interconnection: [Remote Procedure Call]("http://en.wikipedia.org/wiki/Remote_Procedure_Call") over a serial link, DMA controller for bulk transfer
[*][Cache memory]("http://en.wikipedia.org/wiki/Cache_memory"): Instruction: 16KB, Data: 8KB + 16 KB (ScrP)[/LIST] 
[*]Graphics: "Graphics Synthesizer" clocked at 147 MHz[LIST]
[*]Pixel pipelines:16
[*]Video output resolution: variable from 256x224 to 1280x1024 pixels
[*]4 MB [Embedded DRAM]("http://en.wikipedia.org/wiki/Embedded_DRAM") [video memory]("http://en.wikipedia.org/wiki/Video_memory") bandwith at 47GB per second(main system 32 MB can be dedicated into vram)
[*]DRAM Bus bandwidth: 47.0GB per second
[*]DRAM Bus width: 2560-bit (composed of three independent buses: 1024-bit write, 1024-bit read, 512-bit read/write)
[*]Pixel Configuration: RGB:Alpha:Z Buffer (24:8, 15:1 for RGB, 16, 24, or 32-bit Z buffer)
[*]Dedicated connection to: Main CPU and VU1
[*]Overall Pixel fillrate: 16x147 = 23.52(rounded to 2.4)
[*]Pixel fillrate: with no texture, flat shaded 2.4(75,000,000 32pixel real-world triangles)
[*]Pixel fillrate: with 1 full texture(normal skin), Gouraud shaded 1.2(37,750,000 32pixel real-world triangles)
[*]Pixel fillrate: with 2 full textures(normal skin+specular or alpha or other), Gouraud shaded 0.6(18,750,000 32pixel real-world triangles)
[*]Multi-pass rendering ability (four passes: 300M pixels/second)[/LIST] 
[*]Sound: "SPU1+SPU2" (SPU1 is actually the CPU clocked at 8 MHz)[LIST]
[*]Number of voices: 48 hardware channels of ADPCM on SPU2 plus software-mixed channels
[*]Sampling Frequency: 44.1 kHz or 48 kHz (selectable)
[*]Output: [Dolby Digital]("http://en.wikipedia.org/wiki/Dolby_Digital") 5.1 [Surround sound]("http://en.wikipedia.org/wiki/Surround_sound"), [DTS]("http://en.wikipedia.org/wiki/Digital_Theater_System") (cutscenes only), later games achieved analog 5.1 surround during gameplay through [Dolby Pro Logic II]("http://en.wikipedia.org/wiki/Dolby_Pro_Logic#Dolby_Pro_Logic_II")[/LIST] 
[*]I/O Processor[LIST]
[*]CPU Core: Original PlayStation CPU (MIPS R3000A clocked at 33.8688 MHz or 37.5 MHz)
[*]Sub Bus: 32 Bit
[*]Connection to: SPU and CD/DVD controller.[/LIST] 
[*]Interface Types: 2 proprietary PlayStation controller ports (250KHz clock for PS1 and 500KHz for PS2 controllers), 2 proprietary Memory Card slots using [MagicGate]("http://en.wikipedia.org/wiki/MagicGate") [encryption]("http://en.wikipedia.org/wiki/Encryption") (250KHz for PS1 cards, up to 2MHz for PS2 cards), Expansion Bay (PCMCIA on early models for PCMCIA Network Adaptor and External Hard Disk Drive) DEV9 port for Network Adaptor, [Modem]("http://en.wikipedia.org/wiki/Modem") and Internal Hard Disk Drive, [IEEE 1394]("http://en.wikipedia.org/wiki/FireWire") (only in SCPH 10xxx - 3xxxx), [Infrared]("http://en.wikipedia.org/wiki/Infrared") remote control port (SCPH 5000x and newer),[[16]]("http://en.wikipedia.org/wiki/PlayStation_2#_note-11") and 2 [USB]("http://en.wikipedia.org/wiki/Universal_Serial_Bus") 1.1 ports with an OHCI-compatible controller.[/LIST] [LIST]
[*]Disc Drive type: 24x (PlayStation 2 format CD-ROM, PlayStation format CD-ROM) 4x (Supported DVD formats) Region-locked with anti-copy protection (Can't read "Gold Discs" aka normal CD-ROMs)[/LIST] [LIST]
[*]Supported Disc Media: PlayStation 2 format CD-ROM, PlayStation format CD-ROM, [Compact Disc Audio]("http://en.wikipedia.org/wiki/Red_Book_%28audio_CD_standard%29"), PlayStation 2 format DVD-ROM (4.7 GB), [DVD Video]("http://en.wikipedia.org/wiki/DVD_Video") (4.7 GB). Later models are [DVD-9]("http://en.wikipedia.org/wiki/DVD-9") (8.5 GB Dual-Layer), [DVD+RW]("http://en.wikipedia.org/wiki/DVD%2BRW"), and [DVD-RW]("http://en.wikipedia.org/wiki/DVD-RW") compatible.[/quote]

specs[/LIST]

---

### Post by dbbolton on 2006-12-24
from ds linux site:

Run light enough to power a 486DX with 16MB of Ram

---

### Post by mips on 2006-12-24
> **dbbolton said:**
> is it possible ?

No. You would have to port DSL to the MIPS cpu architecture I suppose if you wanted to run it on a PS2.

[http://www.debian.org/ports/mips/](http://www.debian.org/ports/mips/)
[http://playstation2-linux.com/](http://playstation2-linux.com/)
[http://en.wikipedia.org/wiki/PS2_Linux](http://en.wikipedia.org/wiki/PS2_Linux)

---

### Post by dbbolton on 2006-12-24
i checked out the playstation2-linux site, but according to it ps2 linux isn't available in the US anymore.

---

### Post by mips on 2006-12-24
> **dbbolton said:**
> i checked out the playstation2-linux site, but according to it ps2 linux isn't available in the US anymore.

Check Ebay or import from the UK/Europe ?

---

### Post by patrickfromspain on 2006-12-26
mm sorry, but wasn't the playstation 2 based on a pentium 3 700MHz with some nvidia graphics chip and 64mb ram? I know it has been done... using some game to enter linux or something..

---

### Post by Brynster on 2007-01-02
> **patrickfromspain said:**
> mm sorry, but wasn't the playstation 2 based on a pentium 3 700MHz with some nvidia graphics chip and 64mb ram? I know it has been done... using some game to enter linux or something..


Thats was the original XboX

---

### Post by patrickfromspain on 2007-01-03
> **Brynster said:**
> Thats was the original XboX
yes! sorry for the confusion.. that was, as you said, the xbox..

---


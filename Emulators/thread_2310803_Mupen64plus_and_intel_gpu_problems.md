---
title: "Mupen64plus and intel gpu problems"
date: 2016-01-22
forum: Emulators
---

### Post by richfriedland on 2016-01-22
ntegrated Intel GMA 3100 graphicsI am running into the exact same thing. Previously, I used Ubuntu 14.04 with mupen64plus and all worked well. I did a clean install of Ubuntu 15.10 and installed mupen64plus from Software Center. Now, every game I launch gives me an error like what awesomeant04 described. I have been searching high and low for a solution. Any help is greatly appreciated. 

Here is an example of the errors I am seeing:
Video: Enabled hacks for game: 'GOLDENEYE'
Video: Initializing OpenGL Device Context.
Core: Setting 32-bit video mode: 640x480
Core Error: SDL_SetVideoMode failed: Could not create GL context
Video Error: Failed to set 32-bit video mode: 640x480
Core Status: Rom closed.

My machine has integrated Intel GMA 3100 graphics. It is a Compaq HP 7800p Ultra slim form factor.

---

### Post by deadflowr on 2016-01-22
I've moved your post to it's own thread.
Here's a reference for others:
[http://ubuntuforums.org/showthread.php?t=2309583](http://ubuntuforums.org/showthread.php?t=2309583)


Basically I'd say look at the settings in the mupen64plus.conf file, located in ~/.config/mupen64plus.
Primarily the [Video-Rice] section
See if any of the suggestions they layout might help tweak it.


For what it's worth, this is what mine looks like:
```
[Video-Rice]

# Frame Buffer Emulation (0=ROM default, 1=disable)
FrameBufferSetting = 0
# Frequency to write back the frame buffer (0=every frame, 1=every other frame, etc)
FrameBufferWriteBackControl = 0
# Render-to-texture emulation (0=none, 1=ignore, 2=normal, 3=write back, 4=write back and reload)
RenderToTexture = 0
# Control when the screen will be updated (0=ROM default, 1=VI origin update, 2=VI origin change, 3=CI change, 4=first CI change, 5=first primitive draw, 6=before screen clear, 7=after screen drawn)
ScreenUpdateSetting = 1
# Force to use normal alpha blender
NormalAlphaBlender = False
# Use a faster algorithm to speed up texture loading and CRC computation
FastTextureLoading = False
# Use different texture coordinate clamping code
AccurateTextureMapping = True
# Force emulated frame buffers to be in N64 native resolution
InN64Resolution = False
# Try to reduce Video RAM usage (should never be used)
SaveVRAM = False
# Enable this option to have better render-to-texture quality
DoubleSizeForSmallTxtrBuf = False
# Force to use normal color combiner
DefaultCombinerDisable = False
# Enable game-specific settings from INI file
EnableHacks = True
# If enabled, graphics will be drawn in WinFrame mode instead of solid and texture mode
WinFrameMode = False
# N64 Texture Memory Full Emulation (may fix some games, may break others)
FullTMEMEmulation = False
# Enable vertex clipper for fog operations
OpenGLVertexClipper = False
# Enable/Disable SSE optimizations for capable CPUs
EnableSSE = True
# Use GPU vertex shader
EnableVertexShader = False
# If this option is enabled, the plugin will skip every other frame
SkipFrame = False
# If enabled, texture enhancement will be done only for TxtRect ucode
TexRectOnly = False
# If enabled, texture enhancement will be done only for textures width+height<=128
SmallTextureOnly = False
# Enable hi-resolution texture file loading
LoadHiResTextures = False
# Enable texture dumping
DumpTexturesToFiles = False
# Display On-screen FPS
ShowFPS = False
# Use Mipmapping? 0=no, 1=nearest, 2=bilinear, 3=trilinear
Mipmapping = 2
# Enable, Disable or Force fog generation (0=Disable, 1=Enable n64 choose, 2=Force Fog)
FogMethod = 0
# Force to use texture filtering or not (0=auto: n64 choose, 1=force no filtering, 2=force filtering)
ForceTextureFilter = 0
# Primary texture enhancement filter (0=None, 1=2X, 2=2XSAI, 3=HQ2X, 4=LQ2X, 5=HQ4X, 6=Sharpen, 7=Sharpen More, 8=External, 9=Mirrored)
TextureEnhancement = 0
# Secondary texture enhancement filter (0 = none, 1-4 = filtered)
TextureEnhancementControl = 0
# Color bit depth to use for textures (0=default, 1=32 bits, 2=16 bits)
TextureQuality = 0
# Z-buffer depth (only 16 or 32)
OpenGLDepthBufferSetting = 16
# Enable/Disable MultiSampling (0=off, 2,4,8,16=quality)
MultiSampling = 0
# Color bit depth for rendering window (0=32 bits, 1=16 bits)
ColorQuality = 0
# OpenGL level to support (0=auto, 1=OGL_1.1, 2=OGL_1.4, 3=OGL_FRAGMENT_PROGRAM)
OpenGLRenderSetting = 0
# Enable/Disable Anisotropic Filtering for Mipmapping (0=no filtering, 2-16=quality). This is uneffective if Mipmapping is 0. If the given value is to high to be supported by your graphic card, the value will be the highest value your graphic card can support. Better result with Trilinear filtering
AnisotropicFiltering = 0
# Select hi-resolution textures based only on the CRC and ignore format+size information (Glide64 compatibility)
LoadHiResCRCOnly = True
# Mupen64Plus Rice Video Plugin config parameter version number
Version = 1
# If true, use polygon offset values specified below
ForcePolygonOffset = False
# Specifies a scale factor that is used to create a variable depth offset for each polygon
PolygonOffsetFactor = 0
# Is multiplied by an implementation-specific value to create a constant depth offset
PolygonOffsetUnits = 0
```

---

### Post by richfriedland on 2016-01-22
Thank you! I just tried installing m64py and it actually seems to work now. I found it here: [http://sourceforge.net/projects/m64py/?source=typ_redirect](http://sourceforge.net/projects/m64py/?source=typ_redirect)

---


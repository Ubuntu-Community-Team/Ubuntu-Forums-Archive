---
title: "Black screen with game on VMWare"
date: 2007-02-06
forum: Gaming &amp; Leisure
---

### Post by Gibbs on 2007-02-06
Hello,

I know VMWare and other tools aren't brilliant for DirectX games on Linux but I am desperately trying to get this game working. I can log in, mails are sent to my mail folder and I can do everything. 

What's the problem? The entire screen is black (lol). All I can see if the cursor. However if I alt-tab the screen flickers showing the game how it should be for about 0.2 seconds. That's a sign that it can be played in my opinion.

The points are noted about VMWare and it's "experimental" DirectX as not functional or stable:
[LIST]
[*]Pixel and vertex shaders
[*]Multiple vertex streams
[*]Hardware bump-mapping, environment mapping
[*]Projected textures
[*]Textures with one, three, or four dimensions
[/LIST]

I'm going to post the config file here. If anyone can point out something that might be affecting the game or doesn't comply with the list above please tell me. I'm aware that this config is specific engine settings but some words might make sense to someone.

```
"FarZ" "2165"
"VS_SPRITES_NOZ" "128"
"CardDesc" "HAL"
"DetailTextureScale" "1.0"
"LightModelSprites" "1"
"GammaB" "1.000000"
"ElementOpacity" "89"
"VS_PARTICLESYSTEMS" "512"
"FogEnable" "0.000000"
"optimizesurfaces" "1"
"ModelSpecularHighlights" "1"
"GammaG" "1.000000"
"ChatBubbles" "1"
"RunLock" "1"
"WindowOpacity" "85"
"WeaponPerturb" "3.000000"
"windowed" "0"
"VS_SPRITES" "512"
"MS_Enable" "1"
"LightMap" "1"
"ShowMap" "1"
"SoundFilters" "1"
"DOT3BumpMap" "0"
"GammaR" "1.000000"
"VS_POLYGRIDS_TRANSLUCENT" "64"
"MouseSensitivity" "4.000000"
"UseEAX" "0"
"bitdepth" "32"
"CameraDistance" "193.204498"
"HardwareCursor" "1"
"CameraShift" "-0.768897"
"VS_POLYGRIDS" "64"
"Shadows" "0"
"ChatPlaySounds" "0"
"ScreenWidth" "800"
"Trilinear" "1"
"VSyncOnFlip" "1"
"UpdateRateInitted" "1"
"MuzzleLight" "1"
"VS_CANVASES" "32"
"DetailTextures" "1"
"enabledevice" "##mouse"
"ToolTips" "1"
"SoundDriver" "DirectSound"
"VS_CANVASES_TRANSLUCENT" "128"
"EnvMapEnable" "1"
"EnvMapWorld" "1"
"Window_Chat_On" "1.000000"
"MusicVolume" "72.000000"
"Window_Properties_On" "1.000000"
"VS_LINESYSTEMS" "128"
"ForceClear" "1"
"SoundVolume" "88.000000"
"CameraMode" "2.000000"
"BlockTrade" "0"
"InputRate" "12.000000"
"VS_MODELS" "512"
"WeatherEffects" "1"
"GroupOffset0" "-1"
"MipMapBias" "1"
"TextOpacity" "100"
"VS_WORLDMODELS_TRANSLUCENT" "512"
"MouseInvertY" "0"
"VS_LIGHTS" "64"
"CrouchLock" "0"
"ChatSendToSelectedFriends" "1"
"ModelLODOffset" "0"
"ScreenHeight" "600"
"VS_MODELS_TRANSLUCENT" "256"
"TripleBuffer" "1"
"DynamicLight" "1"
"EnvBumpMap" "1"
"ModelAdd" "50 50 50"
"MaxModelLights" "4"
"VS_WORLDMODELS" "512"
```

Thanks for any replies!

---

### Post by conjur3r on 2007-02-08
Well I think you may have encountered vmware's limitations.  It really doesn't have 3d support at this time.  If your game supports setting the video in software mode then you will have much better luck, at the expense of speed.

What's the game called?  Have you tried with wine or cedega?

---


---
title: "[SOLVED] Unreal Gold AFTER Unreal Tournament"
date: 2009-02-18
forum: Gaming &amp; Leisure
---

### Post by AdamShumpisxXx on 2009-02-18
Hello, all! I'd like to introduce myself to these forums humbly. I've been a lurker for about 3 years and have solved every single one of my issues so far just by looking on. So thank you all who have helped without knowing. On to the matter at hand...

I have installed Unreal Tournament GOTY version with the help of your forums (thanks again). I used the native Linux installer provided by Loki. I installed it on my ntfs STORAGE partition that I share with Ubuntu and Linux. The directory looks like this:

/media/STORAGE/Games/UTGOTY

The game runs great and online play is as phenomenal as I remember it. I thought "That went awesome. Let's go for Unreal Gold!" and this is where the problems start. I installed Unreal Gold using the native Linux installer provided by Loki as well. I also installed this on my STORAGE partition and that directory looks like this:

/media/STORAGE/Games/UnrealGold/

Beyond that I got nothing. No matter what file I try to run within the UnrealGold folder I get no errors and nothing starts. I even looked in the created .loki folder within my Home directory but nothing that I edited mattered. So I beg you...PLEASE HELP ME! Thank you all in advance!

---

### Post by AdamShumpisxXx on 2009-02-19
I know this is just a shameless bump but I'm on my knees BEGGING at this point :D. Seriously, any help would be greatly appreciated.

---

### Post by AdamShumpisxXx on 2009-02-19
One more grasping hope at an answer. BUMP! Seriously though...I'll mail a dollar to the first one who solves my problem. Now you KNOW I'm desperate! :(

---

### Post by Butthead on 2009-02-19
Hmm, try installing it under Wine, perhaps? :confused:

---

### Post by AdamShumpisxXx on 2009-02-19
> **Butthead said:**
> Hmm, try installing it under Wine, perhaps? :confused:

I did and was quite unsatisfied with the results. The screen would frequently glitch to a 640x480 window and render GNOME useless until I hit CTRL + ALT + Backspace. Also, I didn't like the screen jumping. Running things through Wine using DirectX is a poor substitute for a good old native Linux install utilizing OpenGL. Thank you for your suggestion regardless. Is there no one out there who has done this before?!?! I'm pretty sure if it's not brought up and solved now it won't be possible for people to play Unreal Gold with this setup as not too many people talk about it anymore :p. 1$ PEOPLE!!!

---

### Post by R33D3M33R on 2009-02-20
Post the contents of your /media/STORAGE/Games/UnrealGold/System/ folder

---

### Post by AdamShumpisxXx on 2009-02-20
```
Default.ini    ucc-bin	    UMenu.int	UnrealI.int	 UPak.int
DefUser.ini    UDSDemo.int  UMenu.u	Unreal.int	 UPak.u
OpenGLDrv.int  UDSDemo.u    unreal-bin	UnrealShare.int
```

Do you need anything else?

---

### Post by Sand &amp; Mercury on 2009-02-21
Just FYI, you can actually play the original Unreal game through Unreal Tournament, using a mod called Oldskool Amp'd. You install the mod, then move all of your .unr files from your Unreal Gold Maps folder to your UT99 GOTY Maps folder, and repeat with the files in the Music Folders. The only downside to this, is that Return To Na Pali isn't supported this way.

You should be able to find Oldskool through some google-fu, but if you can't find a working link, shoot me a PM and I'll see if I can fix you up with it.

---

### Post by AdamShumpisxXx on 2009-02-21
Quick question with that...Will that appear in my mods list? Also, will that in any way, shape, or form interfere with Unreal Tournament? As to say will I have to overwrite anything? Your solution sounds like the 99.99% closest thing to achieving what I want. I would however like Unreal Gold itself to run natively like it should but beggars can't be choosers. PM will be sent shortly. I am still searching for the answer to my original question. Don't give up on me guys! Hahaha...

---

### Post by anjilslaire on 2009-02-21
Here's where to find the mod installer:

[http://icculus.org/~ravage/unreal/unrealgold/](http://icculus.org/~ravage/unreal/unrealgold/)

---

### Post by AdamShumpisxXx on 2009-02-21
> **anjilslaire said:**
> Here's where to find the mod installer:

[http://icculus.org/~ravage/unreal/unrealgold/](http://icculus.org/~ravage/unreal/unrealgold/)

You realize that is a link to download the installer created by Loki which I had already stated I had used, right? So here's what I'm saying. That does not work. I used that exact site and I am where I am because of it. It installs Unreal Gold perfectly as stated before but after installation the game does not run. I should include my computer's specifications as I believe that is a pertinent piece of information I had overlooked previously. They are as follows:

MOBO = ASUS M2R32-MVP
CPU = AMD 64 AthlonX2 6400+
RAM = 4GB G.SKILL PC2-6400
GRAPHICS CARD = ATI Sapphire x1950xtx 512MB GDDR3
DVDRW = ASUS 18X DVDRW DRW-1814BL
HDD = 500GB Seagate SATA 3.0GB/S
FDD = ASUS 3 1/2" Floppy Drive
OS = Ubuntu 8.10 32-Bit Version

---

### Post by AdamShumpisxXx on 2009-02-21
Also, I understand that by me using the 32-Bit version of Ubuntu I can only utilize 3.2GBs of my 4GBs of RAM. I find the 32-Bit version FAR MORE stable and I already have Windows XP Professional x64 installed as the other half of my dual boot configuration which I use ONLY for gaming.

---

### Post by anjilslaire on 2009-02-22
There's no way I could have known that. You didn't specify where you got the Loki installer from, and that front page doesn't mention the Loki installer itself.

Apologies for the goosechase.

---

### Post by AdamShumpisxXx on 2009-02-22
> **AdamShumpisxXx said:**
> I installed Unreal Gold using the native Linux installer provided by Loki as well.

I actually do mention it. I do however realize I don't mention where I got it. I meant to say I already used the Loki installer from that site and from a number of other sites as well and it does not work. Sorry for the confusion. Thank you regardless.

EDIT:
I now realize that you mean the "front page" of the link you gave me and not the "front page" of this thread. Apologies again.

---

### Post by R33D3M33R on 2009-02-22
What happens if you open terminal, and run the ut-bin like this:

./ut-bin

---

### Post by AdamShumpisxXx on 2009-02-22
From what directory? When I run it from the standard starting place terminal opens up in I get:
```

adam@ADAMXXX-UBUNTU:~$ ./ut-bin
bash: ./ut-bin: No such file or directory
adam@ADAMXXX-UBUNTU:~$

```
When I run it from /UTGOTY/System/ Unreal Tournament GOTY runs and I get:
```

GL_EXTENSIONS : GL_AMD_performance_monitor GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_texgen_reflection GL_SGIS_generate_mipmafcntl: Operation not permitted
fcntl: Operation not permitted
p GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control
adam@ADAMXXX-UBUNTU:/media/STORAGE/Games/UTGOTY/System$

```
When I run it from /UnrealGold/System/ I get:
```

adam@ADAMXXX-UBUNTU:/media/STORAGE/Games/UnrealGold/System$ ./ut-bin
bash: ./ut-bin: No such file or directory
adam@ADAMXXX-UBUNTU:/media/STORAGE/Games/UnrealGold/System$ 

```
What steps should I now follow?

---

### Post by AdamShumpisxXx on 2009-02-22
Listen everyone...Thanks for all the help but I am abandoning this thread. I have given up on installing Unreal Gold in favor of just installing the Oldskool Amp'd and Operation: Na Pali umods for Unreal Tournament GOTY. This solution gives the same effect without all the hassle of trying to solve the unsolvable. Thank you for everyone who has led me to this conclusion! :KS

---

### Post by R33D3M33R on 2009-02-23
Sorry, I gave you false instructions. I meant

./unreal-bin

:oops:

---

### Post by AdamShumpisxXx on 2009-02-23
That's OK. I've "solved" the problem. I thank you for your attempt at help. Hopefully people searching for the same answer will see this and recognize it as the better course of action.

---


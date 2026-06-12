---
title: "Video Card for Unity"
date: 2012-01-05
forum: Desktop Environments
---

### Post by paddyjoe on 2012-01-05
I upgraded to Version 11.04, based on my purchase of the Official Ubuntu Book Sixth Edition. When I started it I got the message that I cannot use Unity because my hardware is not adequate. The book says that if I have a video card that is able to handle Unity, the desktop will look like 3.1. 

Obviously my video card cannot handle Unity. I am trying to keep up with the latest version and capability of Ubuntu. Where can I find information on the hardware requirements to handle Unity?

Paddyjoe

Athlone 
Ireland

---

### Post by bluexrider on 2012-01-05
**  [UnityHardwareRequirements]("https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements") **

                           
**UNE Qualification Requirements Table**

    

   **CPU***         
    **ARCH** 
   **RAM**
    **HD** 
    **GPU**** 
    **OpenGL** 
    **GLX** 
    **Display** 
    **Reference** 
    **Minimum**     
   1.66 GHz 
   32 bits

   1GB
   4 GB  
   intel GMA 950 
   1.4 
   1.4 
   1024x600 
   Dell Mini 9 
    **Recommended** 
   1.66 GHz 
   32 bits 
   2GB
   16 GB  
   [GeForce]("https://wiki.ubuntu.com/GeForce") 9400M 
   2.0 
   1.5 
   1280x800 
   HP Mini 311 
  

      
   

   **Software Requirements** 
    **OS** 
    Ubuntu 10.04 LTS (Lucid Lynx) 
    **Kernel Version** 
    2.6.32 
    **X.org Version** 
    1.7.5 
    **OpenGL**
   1.4
    **GLX**
   1.5
  

      
   

   **GPU Driver Requirements** 
    **intel GMA 950** 
    20091221 2009Q4 x86/MMX/SSE2 
    **[GeForce]("https://wiki.ubuntu.com/GeForce") 9400M** 
    195.36.15 Nvidia Certified 
    **Radeon** 
    fglrx ATI Certified 
  
 
**Minimum GPU Requirements**

   Intel Graphics Core    
   Intel® GMA 950 
   Intel® GMA 3000 
   Intel® GMA 3100 
   Intel® GMA X3000 
   Intel® GMA X3100 
    Intel® Chipset         
   945G, 945GM 
   946GZ, Q963, Q965 
   G31, G33, Q33, Q35 
   G965 
   GM965, GL960 
    OpenGL Support         
   1.4 + Extensions 
   1.4 + Extensions 
   1.4 + Extensions 
   1.5 
   1.5 
    Video Memory           
   Up to 256MB 
   Up to 256MB 
   Up to 256MB 
   Up to 384MB 
   Up to 384MB 
    Hardware Vertex Shader 
   No    
   No 
   No 
   Yes 
   Yes 
    GLSL shader            
   No    
   No 
   No 
   No 
   No 
    ARB shader program     
   Yes   
   Yes 
   Yes 
   Yes 
   Yes 
  
 
**Recommended Intel GPU**

   Intel® Chipset 
   G45, GM45, GS45, G43, G41, GL40 Express 
   Core i3-500, Core i3-300M 
   Core i7-600M, Core i5-600, Core i5-500M, Core i5-400M 
    OpenGL Support 
   2.0 
   2.1 
   2.1 
    Video Memory 
   Up to 1.7GB 
   Up to 1.7GB 
   Up to 1.7GB 
    Hardware Vertex Shader 
   Yes 
   Yes 
   Yes 
    GLSL shader 
   Yes 
   Yes 
   Yes 
    ARB shader program 
   Yes 
   Yes 
   Yes 
  
 
**Recommended NVidia GPU**

   NVidia GPU 
   [GeForce]("https://wiki.ubuntu.com/GeForce") 9400M 
   [GeForce]("https://wiki.ubuntu.com/GeForce") 9100M G, [GeForce]("https://wiki.ubuntu.com/GeForce") 9200M G, [GeForce]("https://wiki.ubuntu.com/GeForce") 9300M G 
    OpenGL Support 
   3.2 
   3.2
    Video Memory 
   512M (minimum) 
   512M (minimum)
    Hardware Vertex Shader 
   Yes 
   Yes
    GLSL shader 
   Yes 
   Yes 
    ARB shader program 
   Yes 
   Yes
  
 
**Recommended AMD GPU**

   AMD GPU 
   Radeon HD 2400 Series 
   Radeon HD 3400 Series 
    OpenGL Support 
   3.2 
   3.2 
    Video Memory 
   512M (minimum) 
   512M (minimum) 
    Hardware Vertex Shader 
   Yes 
   Yes 
    GLSL shader 
   Yes 
   Yes 
    ARB shader program 
   Yes 
   Yes 
  
 
**OpenGL Extension requirements**

   **OpenGL Extensions** 
     GL_ARB_framebuffer_object 
     GL_ARB_vertex_program 
     GL_ARB_fragment_program 
     GL_ARB_texture_non_power_of_two 
     GL_ARB_vertex_buffer_object 
     GL_ARB_texture_rectangle 
  
  **Capabilities** 
    

    MAX_TEXTURE_UNITS 
    8 
     MAX_TEXTURE_COORDS_ARB 
   8 
     MAX_TEXTURE_IMAGE_UNITS_ARB 
    16 
     MAX_PROGRAM_TEX_INDIRECTIONS_ARB 
    4 
     MAX_PROGRAM_TEX_INSTRUCTIONS_ARB 
    32 
     MAX_PROGRAM_ALU_INSTRUCTIONS_ARB 
    64 
  

 **: Intel and AMD CPUs are supported. ARM platforms are not yet supported.* 
 ***: Intel, NVidia and ATI GPUs are supported.*
      

   
                          DesktopExperienceTeam/UnityHardwareRequirements  (last edited 2011-04-22 10:23:10 by [didrocks]("https://launchpad.net/%7Edidrocks"))


[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

---

### Post by wildmanne39 on 2012-01-05
Hi, it you might just need to install a video card driver.

Look in additional drivers and see if there is a driver for your video card if so activate it and reboot.
Thanks

---


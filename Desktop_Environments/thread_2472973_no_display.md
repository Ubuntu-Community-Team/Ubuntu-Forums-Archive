---
title: "no display"
date: 2022-03-19
forum: Desktop Environments
---

### Post by bjlockie on 2022-03-19
I moved my desktop and monitor but now I don't have a display.
I can ssh in and I use nomachine (remote deskttop software).
The nomachine is 640x480 though and nvidia x server settings (control panel) says synced to display: unknown.

The end of /var/log/Xorg.0.log says:
```
[     7.777] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     7.777] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     7.777] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     7.777] (--) NVIDIA(GPU-0): 
[     7.777] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.777] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.777] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.777] (--) NVIDIA(GPU-0): 
[     7.777] (--) NVIDIA(GPU-0): DFP-2: disconnected
[     7.777] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[     7.777] (--) NVIDIA(GPU-0): DFP-2: 1440.0 MHz maximum pixel clock
[     7.777] (--) NVIDIA(GPU-0): 
[     7.777] (--) NVIDIA(GPU-0): DFP-3: disconnected
[     7.777] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[     7.777] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[     7.777] (--) NVIDIA(GPU-0): 
[     7.804] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     7.804] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     7.804] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     7.804] (--) NVIDIA(GPU-0): 
[     7.804] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.804] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.804] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.804] (--) NVIDIA(GPU-0): 
[     7.804] (--) NVIDIA(GPU-0): DFP-2: disconnected
[     7.804] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[     7.804] (--) NVIDIA(GPU-0): DFP-2: 1440.0 MHz maximum pixel clock
[     7.804] (--) NVIDIA(GPU-0): 
[     7.804] (--) NVIDIA(GPU-0): DFP-3: disconnected
[     7.804] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[     7.804] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[     7.804] (--) NVIDIA(GPU-0): 
[     7.804] (--) NVIDIA(GPU-0): DFP-0: disconnected

```

I have a raspberry pi on the HDMI input on the monitor and it displays.

I am going to try another DVI cable when I find one.

But, any ideas/guesses of things to try?

```
$ sudo nvidia-xconfig --query-gpu-info                                                      
Number of GPUs: 1                                                                                        
                                                                                                         
GPU #0:                                                                                                  
  Name      : NVIDIA GeForce GTX 1050                                                                    
  UUID      : GPU-bf16034e-f93a-45da-11e2-9fdc0abf7a4a                                                   
  PCI BusID : PCI:7:0:0

  Number of Display Devices: 0
```

This was in /var/log/Xorg.0.log says:
```

[     6.850] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:7:0:0
```
but also this:
```

[     6.851] (II) NVIDIA(0): NVIDIA GPU NVIDIA GeForce GTX 1050 (GP107-A) at PCI:7:0:0
```

```

[     6.851] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     6.851] (==) NVIDIA(0):     will be used as the requested mode.
[     6.851] (==) NVIDIA(0): 
[     6.851] (--) NVIDIA(0): No enabled display devices found; starting anyway because
[     6.851] (--) NVIDIA(0):     AllowEmptyInitialConfiguration is enabled
[     6.851] (II) NVIDIA(0): Validated MetaModes:
[     6.851] (II) NVIDIA(0):     "NULL"
[     6.851] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[     6.851] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in defaul
```

---

### Post by ActionParsnip on 2022-03-19
Did you connect the display to the same port on the video card (If it has multiple)?

---

### Post by bjlockie on 2022-03-19
doh, it was plugged into the motherboard dvi instead of the video card.

---


---
title: "Permanently enable/force NVIDIA/XFCE to open the correct monitor as desktop."
date: 2024-06-25
forum: Desktop Environments
---

### Post by makem2 on 2024-06-25
I have two monitors, one, the main desktop is a Display Port connection, the other is an HDMI connection.

My default desktop was XFCE until I decided I needed Android on my machine.

I installed GNOME desktop and enabled Wayland. I then started Waydroid to give me Android capabilities.

I needed Android to stream my desktop to my LG WebOS TV. Then I found Jellyfin!

Now I would like to keep the setup I currently have as I intend to use Jellyfin on a NAS soon. However, I have created a problem with the dual screen setup.

When I start the machine I am taken to GNOME desktop where I have alternatives ranging from XFCE to GNOME on Wayland. 99% of the time I use XFCE and it just means I sign in on GNOME and am taken to XFCE.

But then I find Nvidia has forgotten that I have a dual screen setup and I can no longer move from screen to screen as if they were joined. I can use sudo nvidia-setting to make the change to the correct screen positions and default desktop but it is forgotten even though I save to XORG and either over write or merge the settings.

As soon as I leave XFCE and return via GNOME (which retains the correct settings) I end up having to use NVIDIA screen setting again.

For some years now I have had occasional problems even in XFCE with forgotten settings whereas Windows 10 never seems to.

I need to find out how to fix the screen default settings in XFCE permanently! Help pleaseeee.

```

makem@makem-22:~$ cat /etc/os-release
PRETTY_NAME="Ubuntu 24.04 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo
makem@makem-22:~$ 

```

```

makem@makem-22:~$ nvidia-smi
Tue Jun 25 22:52:28 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.183.01             Driver Version: 535.183.01   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 3060        Off | 00000000:01:00.0  On |                  N/A |
|  0%   36C    P8              20W / 170W |    388MiB / 12288MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      2583      G   /usr/lib/xorg/Xorg                          302MiB |
|    0   N/A  N/A      2846      G   xfwm4                                         3MiB |
|    0   N/A  N/A      3459      G   ...,262144 --variations-seed-version=1       63MiB |
|    0   N/A  N/A      4924      G   ...usr/lib/thunderbird/thunderbird-bin        9MiB |
+---------------------------------------------------------------------------------------+
makem@makem-22:~$ 

```

```

makem@makem-22:~$ ls /usr/share/xsessions/
gnome.desktop  gnome-xorg.desktop  xfce.desktop  xubuntu.desktop
makem@makem-22:~$

```

```

makem@makem-22:~$ echo $XDG_CURRENT_DESKTOP
XFCE
makem@makem-22:~$ 

```

---


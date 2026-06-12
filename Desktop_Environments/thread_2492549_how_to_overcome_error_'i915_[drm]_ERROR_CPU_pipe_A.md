---
title: "how to overcome error: 'i915 [drm] *ERROR* CPU pipe A FIFO underrun'"
date: 2023-11-14
forum: Desktop Environments
---

### Post by bern1 on 2023-11-14
Hi, 
I've installed Ubuntu 23.10 on Fujitsu S940 Thin Client. I experience a black screen (no video signal on my LG OLED TV) when I change the window system selecting e.g Ubuntu/Ubutu on Xorg/other OpenBox using Gnome login screen. Switching between window system takes relatively a lot of time and usually ends with no video signal
I see errors in dmesg. For example:
```
[COLOR=#000000][FONT=Consolas][ 906.433584] rfkill: input handler enabled[/FONT][/COLOR][ 909.018698] rfkill: input handler disabled
[ 938.928845] rfkill: input handler enabled
[ 939.003426] evict_inodes inode 00000000c830a67a, i_count = 1, was skipped!
[ 939.753134] i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun
[COLOR=#000000][FONT=Consolas][ 942.410612] rfkill: input handler disabled[/FONT][/COLOR]
```

 The only way to have video signal again is to  unplugging the DisplayPort-HDMI cable and plugging it in again.
 These annoying situations appear mainly when I log out a user from one Window system e.g.Ubuntu  and need replug video cable to see Gnome login screen again.
I tried several different DP-HDMI cables but there were no major differences in performance. Reconnecting the video cable is always necessary to have video signal.
See my hardware info:
```
el@akacja:~$ sudo inxi -Fza
System:
  Kernel: 6.5.0-10-generic arch: x86_64 bits: 64 compiler: N/A clocksource: tsc
    available: hpet,acpi_pm parameters: BOOT_IMAGE=/boot/vmlinuz-6.5.0-10-generic
    root=UUID=48e6e571-e6fb-4645-840c-66fa297f6eb0 ro
  Console: pty pts/2 DM: GDM3 v: 45.beta Distro: Ubuntu 23.10 (Mantic Minotaur)

Machine:
  Type: Desktop System: FUJITSU product: FUTRO S940 v: N/A serial: <filter> Chassis: type: 3
    serial: <filter>
  Mobo: FUJITSU model: D3543-A1 v: S26361-D3543-A11 serial: <filter> UEFI: FUJITSU // American
    Megatrends v: 5.0.0.13 R1.13.0 for D3543-A1x date: 09/23/2022

CPU:
  Info: model: Intel Pentium Silver J5005 socket: BGA1023 bits: 64 type: MCP arch: Goldmont Plus
    level: v2 built: 2017 process: Intel 14nm family: 6 model-id: 0x7A (122) stepping: 1
    microcode: 0x3E
  Topology: cpus: 1x cores: 4 smt: <unsupported> cache: L1: 224 KiB desc: d-4x24 KiB; i-4x32 KiB
    L2: 4 MiB desc: 1x4 MiB
  Speed (MHz): avg: 1158 high: 1446 min/max: 800/2800 base/boost: 1500/2700 scaling:
    driver: intel_cpufreq governor: schedutil volts: 1.2 V ext-clock: 100 MHz cores: 1: 1000 2: 998
    3: 1446 4: 1190 bogomips: 11980
  Flags: ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
  
Vulnerabilities:
  Type: gather_data_sampling status: Not affected
  Type: itlb_multihit status: Not affected
  Type: l1tf status: Not affected
  Type: mds status: Not affected
  Type: meltdown mitigation: PTI
  Type: mmio_stale_data status: Not affected
  Type: retbleed status: Not affected
  Type: spec_rstack_overflow status: Not affected
  Type: spec_store_bypass mitigation: Speculative Store Bypass disabled via prctl
  Type: spectre_v1 mitigation: usercopy/swapgs barriers and __user pointer sanitization
  Type: spectre_v2 mitigation: Enhanced / Automatic IBRS, IBPB: conditional, RSB filling, PBRSB-eIBRS: Not affected
  Type: srbds status: Not affected
  Type: tsx_async_abort status: Not affected

Graphics:
  Device-1: Intel GeminiLake [UHD Graphics 605] vendor: Fujitsu Solutions driver: i915 v: kernel
    arch: Gen-9.5 process: Intel 14nm built: 2016-20 ports: active: none off: DP-1
    empty: DP-2,HDMI-A-1,HDMI-A-2 bus-ID: 00:02.0 chip-ID: 8086:3184 class-ID: 0300
  Display: server: X.org v: 1.21.1.7 with: Xwayland v: 23.2.0 compositor: gnome-shell driver: X:
    loaded: intel dri: i965 gpu: i915 tty: 157x38
  Monitor-1: DP-1 model: LG (GoldStar) TV SSCR2 serial: <filter> built: 2022 res: 3840x2160
    dpi: 61 gamma: 1.2 size: 1600x900mm (62.99x35.43") diag: 1836mm (72.3") ratio: 16:9 modes:
    max: 3840x2160 min: 720x400
  API: OpenGL Message: GL data unavailable in console for root.

Audio:
  Device-1: Intel Celeron/Pentium Silver Processor High Definition Audio vendor: Fujitsu Solutions
    driver: snd_hda_intel v: kernel alternate: snd_soc_skl, snd_soc_avs, snd_sof_pci_intel_apl
    bus-ID: 00:0e.0 chip-ID: 8086:3198 class-ID: 0403
  API: ALSA v: k6.5.0-10-generic status: kernel-api tools: alsactl,alsamixer,amixer
  Server-1: PipeWire v: 0.3.79 status: n/a (root, process) with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin
    tools: pactl,pw-cat,pw-cli,wpctl

Network:
  Device-1: Realtek RTL8125 2.5GbE driver: r8169 v: kernel pcie: gen: 2 speed: 5 GT/s lanes: 1
    port: e000 bus-ID: 02:00.0 chip-ID: 10ec:8125 class-ID: 0200
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Fujitsu Solutions
    driver: r8169 v: kernel pcie: gen: 1 speed: 2.5 GT/s lanes: 1 port: d000 bus-ID: 03:00.0
    chip-ID: 10ec:8168 class-ID: 0200
  IF: eno1 state: down mac: <filter>

Drives:
  Local Storage: total: 1.03 TiB used: 12.32 GiB (1.2%)
  ID-1: /dev/sda maj-min: 8:0 vendor: Samsung model: HM100UI family: SpinPoint MT2
    size: 931.51 GiB block-size: physical: 4096 B logical: 512 B sata: 2.6 speed: 3.0 Gb/s tech: HDD
    rpm: 5400 serial: <filter> fw-rev: 0001 temp: 30 C scheme: GPT
  SMART: yes state: enabled health: PASSED on: 11y 51d 8h cycles: 831 Old-Age:
    g-sense error rate: 37193 UDMA CRC errors: 353
  ID-2: /dev/sdb maj-min: 8:16 model: 1Realtek RTL9210B-CG size: 119.24 GiB block-size:
    physical: 512 B logical: 512 B type: USB rev: 3.2 spd: 5 Gb/s lanes: 1 mode: 3.2 gen-1x1
    tech: N/A serial: <filter> drive serial: <filter> fw-rev: 1.00 temp: 46 Celsius C scheme: GPT
  SMART: yes health: PASSED on: 108d 18h cycles: 1,855 read-units: 10,172,755 [5.20 TB]
    written-units: 15,211,216 [7.78 TB]
Partition:
  ID-1: / raw-size: 118.19 GiB size: 115.78 GiB (97.96%) used: 12.32 GiB (10.6%) fs: ext4
    block-size: 4096 B dev: /dev/sdb2 maj-min: 8:18
  ID-2: /boot/efi raw-size: 1.05 GiB size: 1.05 GiB (99.80%) used: 6.1 MiB (0.6%) fs: vfat
    block-size: 512 B dev: /dev/sdb1 maj-min: 8:17

Swap:
  Kernel: swappiness: 60 (default) cache-pressure: 100 (default) zswap: no
  ID-1: swap-1 type: file size: 4 GiB used: 0 KiB (0.0%) priority: -2 file: /swap.img

Sensors:
  System Temperatures: cpu: 43.0 C mobo: N/A
  Fan Speeds (rpm): N/A

Info:
  Processes: 228 Uptime: 1h 55m wakeups: 5 Memory: total: 8 GiB available: 7.55 GiB
  used: 2 GiB (26.5%) igpu: 32 MiB Init: systemd v: 253 target: graphical (5) default: graphical
  tool: systemctl Compilers: gcc: 13.2.0 alt: 13 Packages: 1931 pm: dpkg pkgs: 1924 libs: 1057
  tools: apt,apt-get pm: snap pkgs: 7 Shell: Sudo (sudo) v: 1.9.14p2 default: Bash v: 5.2.15
  running-in: pty pts/2 (SSH) inxi: 3.3.29

```

List of current  i915 parameters below:
```
la@akacja:~$ sudo systool -m i915 -avModule = "i915"


  Attributes:
    coresize            = "4145152"
    initsize            = "0"
    initstate           = "live"
    refcnt              = "4"
    srcversion          = "F3D6969CC3C2B3BAB38706E"
    taint               = ""
    uevent              = <store method only>


  Parameters:
    disable_display     = "N"
    disable_power_well  = "-1"
    dmc_firmware_path   = "(null)"
    edp_vswing          = "0"
    enable_dc           = "-1"
    enable_dp_mst       = "Y"
    enable_dpcd_backlight= "-1"
    enable_dpt          = "Y"
    enable_fbc          = "-1"
    enable_guc          = "2"
    enable_gvt          = "N"
    enable_hangcheck    = "Y"
    enable_ips          = "1"
    enable_psr2_sel_fetch= "Y"
    enable_psr          = "-1"
    enable_sagv         = "Y"
    error_capture       = "Y"
    fastboot            = "-1"
    force_probe         = ""
    force_reset_modeset_test= "N"
    gsc_firmware_path   = "(null)"
    guc_firmware_path   = "(null)"
    guc_log_level       = "-1"
    huc_firmware_path   = "(null)"
    invert_brightness   = "0"
    lmem_bar_size       = "0"
    lmem_size           = "0"
    load_detect_test    = "N"
    lvds_channel_mode   = "0"
    memtest             = "N"
    mitigations         = "auto"
    mmio_debug          = "0"
    modeset             = "-1"
    nuclear_pageflip    = "N"
    panel_use_ssc       = "-1"
    psr_safest_params   = "N"
    request_timeout_ms  = "20000"
    reset               = "3"
    vbt_firmware        = "(null)"
    vbt_sdvo_panel_type = "-1"
    verbose_state_checks= "Y"


  Sections:
    .altinstr_aux       = "0xffffffffc0b1b61e"
    .altinstr_replacement= "0xffffffffc0b1b3d6"
    .altinstructions    = "0xffffffffc0c2c2f8"
    .bss                = "0xffffffffc0b64c80"
    .call_sites         = "0xffffffffc0cc73a4"
    .data..read_mostly  = "0xffffffffc0b5fd80"
    .data.once          = "0xffffffffc0b5fd10"
    .data               = "0xffffffffc0b2cde0"
    .exit.data          = "0xffffffffc0b5fe50"
    .exit.text          = "0xffffffffc0b1b340"
    .export_symbol      = "0xffffffffc0cedda8"
    .gnu.linkonce.this_module= "0xffffffffc0b64780"
    .init.data          = "0xffffffffc0cf0000"
    .init.text          = "0xffffffffc0742000"
    .note.Linux         = "0xffffffffc0c2c024"
    .note.gnu.build-id  = "0xffffffffc0c2c000"
    .parainstructions   = "0xffffffffc0cedad0"
    .ref.data           = "0xffffffffc0b62860"
    .retpoline_sites    = "0xffffffffc0cb948c"
    .return_sites       = "0xffffffffc0cbf50c"
    .rodata             = "0xffffffffc0c2cce0"
    .rodata.cst2        = "0xffffffffc0cedd90"
    .rodata.str1.1      = "0xffffffffc0caa082"
    .rodata.str1.8      = "0xffffffffc0c68db0"
    .smp_locks          = "0xffffffffc0cb7f08"
    .static_call.text   = "0xffffffffc0b1b654"
    .static_call_sites  = "0xffffffffc0b5fe90"
    .strtab             = "0xffffffffc0d571c0"
    .symtab             = "0xffffffffc0cf0008"
    .text               = "0xffffffffc08fb000"
    .text.unlikely      = "0xffffffffc0b05ecd"
    __bpf_raw_tp_map    = "0xffffffffc0b62180"
    __bug_table         = "0xffffffffc0b1d000"
    __dyndbg_classes    = "0xffffffffc0b5fe58"
    __ex_table          = "0xffffffffc0cee170"
    __jump_table        = "0xffffffffc073f000"
    __kcrctab_gpl       = "0xffffffffc0c2c24c"
    __ksymtab_gpl       = "0xffffffffc0c2c054"
    __ksymtab_strings   = "0xffffffffc0cee7b2"
    __mcount_loc        = "0xffffffffc0c5dcd1"
    __param             = "0xffffffffc0ced468"
    __patchable_function_entries= "0xffffffffc0b21740"
    __tracepoints_ptrs  = "0xffffffffc0cee218"
    __tracepoints_strings= "0xffffffffc0cee2e0"
    __tracepoints       = "0xffffffffc0b63700"
    _ftrace_events      = "0xffffffffc0b62700"
```
Is there any way to work around these errors?

---


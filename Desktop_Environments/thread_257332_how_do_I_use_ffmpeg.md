---
title: "how do I use ffmpeg?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by maddbaron on 2006-09-14
I have it installed but have no idea how to use it to convert video files. I entered ffmeg in terminal and got this:
> maddbaron@baronnet:~$ ffmpeg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
usage: ffmpeg [[infile options] -i infile]... {[outfile options] outfile}...
Hyper fast Audio and Video encoder

Main options:
-L                  show license
-h                  show help
-version            show version
-formats            show available formats, codecs, protocols, ...
-f fmt              force format
-img img_fmt        force image format
-i filename         input file name
-y                  overwrite output files
-t duration         set the recording time
-fs limit_size      set the limit file size
-ss time_off        set the start time offset
-itsoffset time_off  set the input ts offset
-title string       set the title
-timestamp time     set the timestamp
-author string      set the author
-copyright string   set the copyright
-comment string     set the comment
-v verbose          control amount of logging
-target type        specify target file type ("vcd", "svcd", "dvd", "dv", "pal-vcd", "ntsc-svcd", ...)
-dframes number     set the number of data frames to record
-scodec codec       force subtitle codec ('copy' to copy stream)
-newsubtitle        add a new subtitle stream to the current output stream
-slang code         set the ISO 639 language code (3 letters) of the current subtitle stream

Video options:
-b bitrate          set video bitrate (in kbit/s)
-vframes number     set the number of video frames to record
-r rate             set frame rate (Hz value, fraction or abbreviation)
-s size             set frame size (WxH or abbreviation)
-aspect aspect      set aspect ratio (4:3, 16:9 or 1.3333, 1.7777)
-croptop size       set top crop band size (in pixels)
-cropbottom size    set bottom crop band size (in pixels)
-cropleft size      set left crop band size (in pixels)
-cropright size     set right crop band size (in pixels)
-padtop size        set top pad band size (in pixels)
-padbottom size     set bottom pad band size (in pixels)
-padleft size       set left pad band size (in pixels)
-padright size      set right pad band size (in pixels)
-padcolor color     set color of pad bands (Hex 000000 thru FFFFFF)
-vn                 disable video
-bt tolerance       set video bitrate tolerance (in kbit/s)
-maxrate bitrate    set max video bitrate tolerance (in kbit/s)
-minrate bitrate    set min video bitrate tolerance (in kbit/s)
-bufsize size       set ratecontrol buffer size (in kByte)
-vcodec codec       force video codec ('copy' to copy stream)
-sameq              use same video quality as source (implies VBR)
-pass n             select the pass number (1 or 2)
-passlogfile file   select two pass log file name
-newvideo           add a new video stream to the current output stream

Advanced Video options:
-pix_fmt format     set pixel format
-g gop_size         set the group of picture size
-intra              use only intra frames
-vdt n              discard threshold
-qscale q           use fixed video quantiser scale (VBR)
-qmin q             min video quantiser scale (VBR)
-qmax q             max video quantiser scale (VBR)
-lmin lambda        min video lagrange factor (VBR)
-lmax lambda        max video lagrange factor (VBR)
-mblmin q           min macroblock quantiser scale (VBR)
-mblmax q           max macroblock quantiser scale (VBR)
-qdiff q            max difference between the quantiser scale (VBR)
-qblur blur         video quantiser scale blur (VBR)
-qsquish squish     how to keep quantiser between qmin and qmax (0 = clip, 1 = use differentiable function)
-qcomp compression  video quantiser scale compression (VBR)
-rc_init_cplx complexity  initial complexity for 1-pass encoding
-b_qfactor factor   qp factor between p and b frames
-i_qfactor factor   qp factor between p and i frames
-b_qoffset offset   qp offset between p and b frames
-i_qoffset offset   qp offset between p and i frames
-ibias bias         intra quant bias
-pbias bias         inter quant bias
-rc_eq equation     set rate control equation
-rc_override override  rate control override for specific intervals
-me method          set motion estimation method
-me_threshold       motion estimaton threshold
-mb_threshold       macroblock threshold
-er n               set error resilience
-ec bit_mask        set error concealment
-bf frames          use 'frames' B frames
-preme              pre motion estimation
-lumi_mask          luminance masking
-dark_mask          darkness masking
-scplx_mask         spatial complexity masking
-tcplx_mask         temporal complexity masking
-p_mask             inter masking
-bug param          workaround not auto detected encoder bugs
-strict strictness  how strictly to follow the standards
-deinterlace        deinterlace pictures
-psnr               calculate PSNR of compressed frames
-vstats             dump video coding statistics to file
-vhook module       insert video processing module
-intra_matrix matrix  specify intra matrix coeffs
-inter_matrix matrix  specify inter matrix coeffs
-top                top=1/bottom=0/auto=-1 field first
-nr                 noise reduction
-qns                quantization noise shaping
-sc_threshold threshold  scene change threshold
-me_range range     limit motion vectors range (1023 for DivX player)
-dc precision       intra_dc_precision
-coder              coder type
-context            context model
-pred               prediction method
-nssew              weight
-mepc factor (1.0 = 256)  motion estimation bitrate penalty compensation
-vtag fourcc/tag    force video tag/fourcc
-skip_threshold threshold  frame skip threshold
-skip_factor factor  frame skip factor
-skip_exp exponent  frame skip exponent
-genpts             generate pts

Audio options:
-aframes number     set the number of audio frames to record
-ab bitrate         set audio bitrate (in kbit/s)
-aq quality         set audio quality (codec-specific)
-ar rate            set audio sampling rate (in Hz)
-ac channels        set number of audio channels
-an                 disable audio
-acodec codec       force audio codec ('copy' to copy stream)
-vol volume         change audio volume (256=normal)
-newaudio           add a new audio stream to the current output stream
-alang code         set the ISO 639 language code (3 letters) of the current audio stream

Advanced Audio options:
-atag fourcc/tag    force audio tag/fourcc

Subtitle options:
-scodec codec       force subtitle codec ('copy' to copy stream)
-newsubtitle        add a new subtitle stream to the current output stream
-slang code         set the ISO 639 language code (3 letters) of the current subtitle stream

Audio/Video grab options:
-vd device          set video grab device
-vc channel         set video grab channel (DV1394 only)
-tvstd standard     set television standard (NTSC, PAL (SECAM))
-ad device          set audio device
-grab format        request grabbing using
-gd device          set grab device

Advanced options:
-map file:stream[:syncfile:syncstream]  set input stream mapping
-map_meta_data outfile:infile  set meta data information of outfile from infile
-benchmark          add timings for benchmarking
-dump               dump each input packet
-hex                when dumping packets, also dump the payload
-re                 read input at native frame rate
-loop               loop (current only works with images)
-loop_output        number of times to loop output in formats that support looping (0 loops forever)
-threads count      thread count
-vsync              video sync method
-async              audio sync method
-vglobal            video global header storage type
-copyts             copy timestamps
-shortest           finish encoding within shortest input
-b_strategy strategy  dynamic b frame selection strategy
-ps size            set packet size in bits
-error rate         error rate
-muxrate rate       set mux rate
-packetsize size    set packet size
-muxdelay seconds   set the maximum demux-decode delay
-muxpreload seconds  set the initial demux-decode delay
AVCodecContext AVOptions:
-bit_rate          E.VA. (null)
-bit_rate_tolerance E.V.. (null)
-flags             EDVA. (null)
-mv4               E.V.. use four motion vector by macroblock (mpeg4)
-obmc              E.V.. use overlapped block motion compensation (h263+)
-qpel              E.V.. use 1/4 pel motion compensation
-loop              E.V.. use loop filter
-gmc               E.V.. use gmc
-mv0               E.V.. always try a mb with mv=<0,0>
-part              E.V.. use data partitioning
-gray              EDV.. only decode/encode grayscale
-psnr              E.V.. error[?] variables will be set during encoding
-naq               E.V.. normalize adaptive quantization
-ildct             E.V.. use interlaced dct
-low_delay         .DV.. force low delay
-alt               E.V.. enable alternate scantable (mpeg2/mpeg4)
-trell             E.V.. use trellis quantization
-bitexact          EDVAS use only bitexact stuff (except (i)dct)
-aic               E.V.. h263 advanced intra coding / mpeg4 ac prediction
-umv               E.V.. use unlimited motion vectors
-cbp               E.V.. use rate distortion optimization for cbp
-qprd              E.V.. use rate distortion optimization for qp selectioon
-aiv               E.V.. h263 alternative inter vlc
-slice             E.V.. (null)
-ilme              E.V.. interlaced motion estimation
-scan_offset       E.V.. will reserve space for svcd scan offset user data
-cgop              E.V.. (null)
-fast              E.V.. allow non spec compliant speedup tricks
-sgop              E.V.. strictly enforce gop size
-noout             E.V.. skip bitstream encoding
-local_header      E.V.. place global headers at every keyframe instead of in extradata
-me_method         E.V.. (null)
-gop_size          E.V.. (null)
-qcompress         E.V.. (null)
-qblur             E.V.. (null)
-qmin              E.V.. (null)
-qmax              E.V.. (null)
-max_qdiff         E.V.. (null)
-max_b_frames      E.V.. (null)
-b_quant_factor    E.V.. (null)
-rc_strategy       E.V.. (null)
-b_frame_strategy  E.V.. (null)
-hurry_up          .DV.. (null)
-bugs              .DV.. (null)
-autodetect        .DV.. (null)
-old_msmpeg4       .DV.. (null)
-xvid_ilace        .DV.. (null)
-ump4              .DV.. (null)
-no_padding        .DV.. (null)
-amv               .DV.. (null)
-ac_vlc            .DV.. (null)
-qpel_chroma       .DV.. (null)
-std_qpel          .DV.. (null)
-qpel_chroma2      .DV.. (null)
-direct_blocksize  .DV.. (null)
-edge              .DV.. (null)
-hpel_chroma       .DV.. (null)
-dc_clip           .DV.. (null)
-ms                .DV.. (null)
-lelim             E.V.. single coefficient elimination threshold for luminance (negative values also consider dc coefficient)
-celim             E.V.. single coefficient elimination threshold for chrominance (negative values also consider dc coefficient)
-strict            E.V.. (null)
-very              E.V.. (null)
-strict            E.V.. (null)
-normal            E.V.. (null)
-inofficial        E.V.. (null)
-experimental      E.V.. (null)
-b_quant_offset    E.V.. (null)
-error_resilience  .DV.. (null)
-careful           .DV.. (null)
-compliant         .DV.. (null)
-aggressive        .DV.. (null)
-very_aggressive   .DV.. (null)
-mpeg_quant        E.V.. (null)
-rc_qsquish        E.V.. (null)
-rc_qmod_amp       E.V.. (null)
-rc_qmod_freq      E.V.. (null)
-rc_eq             E.V.. (null)
-rc_max_rate       E.V.. (null)
-rc_min_rate       E.V.. (null)
-rc_buffer_size    E.V.. (null)
-rc_buf_aggressivity E.V.. (null)
-i_quant_factor    E.V.. (null)
-i_quant_offset    E.V.. (null)
-rc_initial_cplx   E.V.. (null)
-dct               E.V.. (null)
-auto              E.V.. (null)
-fastint           E.V.. (null)
-int               E.V.. (null)
-mmx               E.V.. (null)
-mlib              E.V.. (null)
-altivec           E.V.. (null)
-faan              E.V.. (null)
-lumi_mask         E.V.. (null)
-tcplx_mask        E.V.. (null)
-scplx_mask        E.V.. (null)
-p_mask            E.V.. (null)
-dark_mask         E.V.. (null)
-idct              EDV.. (null)
-auto              EDV.. (null)
-int               EDV.. (null)
-simple            EDV.. (null)
-simplemmx         EDV.. (null)
-libmpeg2mmx       EDV.. (null)
-ps2               EDV.. (null)
-mlib              EDV.. (null)
-arm               EDV.. (null)
-altivec           EDV.. (null)
-sh4               EDV.. (null)
-simplearm         EDV.. (null)
-h264              EDV.. (null)
-vp3               EDV.. (null)
-ipp               EDV.. (null)
-xvidmmx           EDV.. (null)
-ec                .DV.. (null)
-guess_mvs         .DV.. (null)
-deblock           .DV.. (null)
-pred              E.V.. (null)
-left              E.V.. (null)
-plane             E.V.. (null)
-median            E.V.. (null)
-aspect            E.V.. (null)
-debug             EDVAS print specific debug info
-pict              .DV.. (null)
-rc                E.V.. (null)
-bitstream         .DV.. (null)
-mb_type           .DV.. (null)
-qp                .DV.. (null)
-mv                .DV.. (null)
-dct_coeff         .DV.. (null)
-skip              .DV.. (null)
-startcode         .DV.. (null)
-pts               .DV.. (null)
-er                .DV.. (null)
-mmco              .DV.. (null)
-bugs              .DV.. (null)
-vis_qp            .DV.. (null)
-vis_mb_type       .DV.. (null)
-vismv             .DV.. visualize motion vectors
-pf                .DV.. (null)
-bf                .DV.. (null)
-bb                .DV.. (null)
-mb_qmin           E.V.. (null)
-mb_qmax           E.V.. (null)
-cmp               E.V.. full pel me compare function
-subcmp            E.V.. sub pel me compare function
-mbcmp             E.V.. macroblock compare function
-ildctcmp          E.V.. interlaced dct compare function
-dia_size          E.V.. (null)
-last_pred         E.V.. (null)
-preme             E.V.. (null)
-precmp            E.V.. pre motion estimation compare function
-sad               E.V.. (null)
-sse               E.V.. (null)
-satd              E.V.. (null)
-dct               E.V.. (null)
-psnr              E.V.. (null)
-bit               E.V.. (null)
-rd                E.V.. (null)
-zero              E.V.. (null)
-vsad              E.V.. (null)
-vsse              E.V.. (null)
-nsse              E.V.. (null)
-w53               E.V.. (null)
-w97               E.V.. (null)
-dctmax            E.V.. (null)
-chroma            E.V.. (null)
-pre_dia_size      E.V.. (null)
-subq              E.V.. (null)
-me_range          E.V.. (null)
-ibias             E.V.. (null)
-pbias             E.V.. (null)
-coder             E.V.. (null)
-vlc               E.V.. (null)
-ac                E.V.. (null)
-context_model     E.V.. (null)
-mbd               E.V.. (null)
-simple            E.V.. (null)
-bits              E.V.. (null)
-rd                E.V.. (null)
-sc_threshold      E.V.. (null)
-lmin              E.V.. min lagrange factor
-lmax              E.V.. max lagrange factor
-noise_reduction   E.V.. (null)
-rc_init_occupancy E.V.. (null)
-inter_threshold   E.V.. (null)
-antialias         .DV.. (null)
-auto              .DV.. (null)
-fastint           .DV.. (null)
-int               .DV.. (null)
-float             .DV.. (null)
-qns               E.V.. (null)
-thread_count      EDV.. (null)
-dc                E.V.. (null)
-nsse_weight       E.V.. (null)
-skip_top          .DV.. (null)
-skip_bottom       .DV.. (null)
-profile           E.VA. (null)
-unknown           E.VA. (null)
-level             E.VA. (null)
-unknown           E.VA. (null)
-lowres            .DV.. (null)
-frame_skip_threshold E.V.. (null)
-frame_skip_factor E.V.. (null)
-frame_skip_exp    E.V.. (null)
-skipcmp           E.V.. frame skip comapare function
-border_mask       E.V.. (null)
-mb_lmin           E.V.. (null)
-mb_lmax           E.V.. (null)
-me_penalty_compensation E.V.. (null)


what do I do? there are some files i'd love to convert.

---

### Post by cwaldbieser on 2006-09-14
> **maddbaron said:**
> I have it installed but have no idea how to use it to convert video files. I entered ffmeg in terminal and got this:


what do I do? there are some files i'd love to convert.

The simplest kind of thing to do is:
```

$ ffmpeg -i inputfile.avi outfile.mpeg

```
You basically give it an input file and an output file, and let it try to guess the formats you want by the filename extensions.  There loads more options.  The above is about as basic as it gets.

---

### Post by maddbaron on 2006-09-14
> **cwaldbieser said:**
> The simplest kind of thing to do is:
```

$ ffmpeg -i inputfile.avi outfile.mpeg

```
You basically give it an input file and an output file, and let it try to guess the formats you want by the filename extensions.  There loads more options.  The above is about as basic as it gets.

thank you... one more question can i use this to convert to wmv or rmvb files since those are smaller than mpeg and avi files?

thank you again i will try to test it out.

:D

---

### Post by cwaldbieser on 2006-09-15
> **maddbaron said:**
> thank you... one more question can i use this to convert to wmv or rmvb files since those are smaller than mpeg and avi files?

thank you again i will try to test it out.

:D

```

$ ffmpeg -formats | less

```

This should show you all the formats that ffmpeg supports.

---

### Post by rickc on 2006-09-16
I've tried using the program and it seems to freeze 80-98% in. I have an ok machine, not too sure why. AMD 2800XP 1 gig of DDR ram DFI Landparty mobo
Is this normal? I have the newest ver installed...

---

### Post by Quiane on 2007-10-03
how do i get ffmpeg to work with floola?? I try the conversion tool floola comes with and it just closes the box and goes back to the add files window.
I'm running feisty fawn...any help would be greatly apprecated!!!

---


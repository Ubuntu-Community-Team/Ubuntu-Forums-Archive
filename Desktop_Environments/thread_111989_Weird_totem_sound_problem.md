---
title: "Weird totem sound problem"
date: 2006-01-03
forum: Desktop Environments
---

### Post by lifesizejesus on 2006-01-03
For some reason totem-xine wont play any sound on some avi videos. When I run totem using sudo, the same videos play just fine (including audio).

The videos that have this problem all use audio codec "A/52 2.0 (dolby)". Here is the full console output from totem, when playing the file as normal user:
```

load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_arts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_dxr3_video.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_dxr3_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_real_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_speex.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_theora.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_vorbis.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_fli.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_gnome_vfs.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_smb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_aa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_caca.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_xv.so found
init class succeeded
gnome_vfs init_input_class
params.c:OpenConfFile() - Unable to open configuration file "/home/mikko/.smb/smb.conf":
        No such file or directory
Using netbios name JEKKU.
Using workgroup MSHOME.
video_out_xv: using Xv port 270 from adaptor NV17 Video Texture for hardware colorspace conversion and scaling.
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.
x11osd: unscaled overlay created (XShape mode).
video_out: thread created
audio_alsa_out : supported modes are 8bit 16bit 24bit 32bit mono stereo (4-channel not enabled in xine config) (4.1-channel not enabled in xine config) (5-channel not enabled in xine config) 5.1-channel a/52 and DTS pass-through
audio_out: thread created
xine_stream_new
video_out_xv: VO_PROP_INTERLACED(1)
xine: found input plugin  : file input plugin
load_plugins: probing demux 'anx'
load_plugins: probing demux 'asf'
load_plugins: probing demux 'aud'
load_plugins: probing demux 'aiff'
load_plugins: probing demux 'cdda'
load_plugins: probing demux 'flac'
load_plugins: probing demux 'nsf'
load_plugins: probing demux 'realaudio'
load_plugins: probing demux 'snd'
load_plugins: probing demux 'voc'
load_plugins: probing demux 'vox'
load_plugins: probing demux 'wav'
load_plugins: probing demux 'mod'
TEST mod decode
load_plugins: probing demux 'avi'
failed to read 8 bytes at pos 367286272
demux_avi: 66147 frames
xine: found demuxer plugin: AVI/RIFF demux plugin
demux_avi: audio format[0] = 0x2000
demux_avi: audio type AC3 (wFormatTag 0x2000)
video discontinuity #1, type is 0, disc_off 0
waiting for audio discontinuity #1
audio discontinuity #1, type is 0, disc_off 0
waiting for in_discontinuity update #1
vpts adjusted with prebuffer to 136070
demux_avi: video codec is 'Microsoft MPEG-4 v3'
load_plugins: plugin ffmpegvideo will be used for video streamtype 05.
load_plugins: plugin a/52 will be used for audio streamtype 00.
audio_alsa_out:open pause_resume=1
output sample rate 48000
xine_play
ao_flush (loop running: 1)
start pos is 0, start time is 0
video_pts = 0
video discontinuity #2, type is 3, disc_off 0
waiting for audio discontinuity #2
audio discontinuity #2, type is 3, disc_off 0
waiting for in_discontinuity update #2
vpts adjusted with prebuffer to 153941
ffmpeg_video_dec: direct rendering enabled
play_internal ...done
** Message: Couldn't initialize lirc.

video discontinuity #3, type is 3, disc_off 3600
waiting for audio discontinuity #3
audio discontinuity #3, type is 3, disc_off 3600
waiting for in_discontinuity update #3
vpts adjusted with prebuffer to 170266
video jump
audio jump, diff=-10800
fixing sound card drift by -2831 pts
fixing sound card drift by -2122 pts
fixing sound card drift by -1591 pts

```

I have the same problem with playing DVDs, but that doesn't bother me much, since I use ogle to play DVDs anyway. Ogle works perfectly. 

Any help would be appreciated..

---


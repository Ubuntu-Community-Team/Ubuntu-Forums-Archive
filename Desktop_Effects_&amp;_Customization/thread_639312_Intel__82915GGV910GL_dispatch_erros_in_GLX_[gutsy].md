---
title: "Intel  82915G/GV/910GL dispatch erros in GLX [gutsy]"
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by dashinganicool007 on 2007-12-13
I have been trying to run compiz since long, and finally got success. Though here's the output of glxinfo:

> 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915G 20050225 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
GetVertexAttribPointervARB -> 667 != 591
DISPATCH ERROR! glGetProgramStringNV -> 664 != 586
DISPATCH ERROR! glVertexAttribs4dvNV -> 717 != 638
DISPATCH ERROR! glProgramParameters4dvNV -> 677 != 598
DISPATCH ERROR! glVertexAttrib1fNV -> 683 != 758
DISPATCH ERROR! glVertexAttrib4dNV -> 699 != 774
DISPATCH ERROR! glVertexAttribs4ubvNV -> 720 != 641
DISPATCH ERROR! glVertexAttribs3svNV -> 716 != 637
DISPATCH ERROR! glVertexAttrib1sNV -> 685 != 760
DISPATCH ERROR! glBindProgramARB -> 658 != 579
DISPATCH ERROR! glAreProgramsResidentNV -> 657 != 578
DISPATCH ERROR! glVertexAttrib3dvNV -> 694 != 769
DISPATCH ERROR! glVertexAttrib1dNV -> 681 != 756
DISPATCH ERROR! glVertexAttribs4svNV -> 719 != 640
DISPATCH ERROR! glVertexAttribs1svNV -> 710 != 631
DISPATCH ERROR! glGenProgramsARB -> 661 != 582
DISPATCH ERROR! glVertexAttrib4dvNV -> 700 != 775
DISPATCH ERROR! glSampleCoverage -> 434 != 412
DISPATCH ERROR! glPointParameterf -> 576 != 458
DISPATCH ERROR! glPointParameterfv -> 577 != 459
DISPATCH ERROR! glCompressedTexSubImage2D -> 439 != 558
DISPATCH ERROR! glCompressedTexImage3D -> 437 != 554
DISPATCH ERROR! glCompressedTexImage1D -> 435 != 556
DISPATCH ERROR! glCompressedTexSubImage1D -> 438 != 559
DISPATCH ERROR! glCompressedTexSubImage3D -> 440 != 557
DISPATCH ERROR! glCompressedTexImage2D -> 436 != 555
DISPATCH ERROR! glGetCompressedTexImage -> 441 != 560
DISPATCH ERROR! glGetBufferSubData -> 506 != 695
DISPATCH ERROR! glBufferSubData -> 501 != 690
DISPATCH ERROR! glBufferData -> 500 != 689
DISPATCH ERROR! glGetBufferPointerv -> 505 != 694
DISPATCH ERROR! glGetBufferParameteriv -> 504 != 693
DISPATCH ERROR! glMapBuffer -> 508 != 697
DISPATCH ERROR! glIsBuffer -> 507 != 696
DISPATCH ERROR! glDeleteBuffers -> 502 != 691
DISPATCH ERROR! glUnmapBuffer -> 509 != 698
DISPATCH ERROR! glBindBuffer -> 499 != 688
DISPATCH ERROR! glGenBuffers -> 503 != 692
DISPATCH ERROR! glProgramEnvParameter4dvARB -> 454 != 669
DISPATCH ERROR! glVertexAttrib2fARB -> 470 != 611
DISPATCH ERROR! glVertexAttrib3fARB -> 476 != 617
DISPATCH ERROR! glVertexAttrib1svARB -> 467 != 608
DISPATCH ERROR! glVertexAttrib4NusvARB -> 486 != 662
DISPATCH ERROR! glDisableVertexAttribArrayARB -> 442 != 666
DISPATCH ERROR! glProgramLocalParameter4dARB -> 457 != 672
DISPATCH ERROR! glVertexAttrib1fARB -> 464 != 605
DISPATCH ERROR! glVertexAttrib4NbvARB -> 480 != 659
DISPATCH ERROR! glVertexAttrib1sARB -> 466 != 607
DISPATCH ERROR! glGetProgramLocalParameterfvARB -> 447 != 679
DISPATCH ERROR! glVertexAttrib3dvARB -> 475 != 616
DISPATCH ERROR! glProgramEnvParameter4fvARB -> 456 != 671
DISPATCH ERROR! glGetVertexAttribivARB -> 452 != 590
DISPATCH ERROR! glVertexAttrib4ivARB -> 492 != 655
DISPATCH ERROR! glVertexAttrib4bvARB -> 487 != 654
DISPATCH ERROR! glVertexAttrib3dARB -> 474 != 615
DISPATCH ERROR! glVertexAttrib4fARB -> 490 != 623
DISPATCH ERROR! glVertexAttrib4fvARB -> 491 != 624
DISPATCH ERROR! glProgramLocalParameter4dvARB -> 458 != 673
DISPATCH ERROR! glVertexAttrib4usvARB -> 497 != 657
DISPATCH ERROR! glVertexAttrib2dARB -> 468 != 609
DISPATCH ERROR! glVertexAttrib1dvARB -> 463 != 604
DISPATCH ERROR! glGetVertexAttribfvARB -> 451 != 589
DISPATCH ERROR! glVertexAttrib4ubvARB -> 495 != 656
DISPATCH ERROR! glProgramEnvParameter4fARB -> 455 != 670
DISPATCH ERROR! glVertexAttrib4sARB -> 493 != 625
DISPATCH ERROR! glVertexAttrib2dvARB -> 469 != 610
DISPATCH ERROR! glVertexAttrib2fvARB -> 471 != 612
DISPATCH ERROR! glVertexAttrib4NivARB -> 481 != 661
DISPATCH ERROR! glGetProgramStringARB -> 448 != 681
DISPATCH ERROR! glVertexAttrib4NuivARB -> 485 != 663
DISPATCH ERROR! glIsProgramARB -> 671 != 592
DISPATCH ERROR! glProgramEnvParameter4dARB -> 453 != 668
DISPATCH ERROR! glVertexAttrib1dARB -> 462 != 603
DISPATCH ERROR! glVertexAttrib3svARB -> 479 != 620
DISPATCH ERROR! glGetVertexAttribdvARB -> 450 != 588
DISPATCH ERROR! glVertexAttrib4dvARB -> 489 != 622
DISPATCH ERROR! glVertexAttribPointerARB -> 498 != 664
DISPATCH ERROR! glVertexAttrib4NsvARB -> 482 != 660
DISPATCH ERROR! glVertexAttrib3fvARB -> 477 != 618
DISPATCH ERROR! glVertexAttrib4NubARB -> 483 != 627
DISPATCH ERROR! glGetProgramEnvParameterfvARB -> 445 != 677
DISPATCH ERROR! glProgramLocalParameter4fvARB -> 460 != 675
DISPATCH ERROR! glDeleteProgramsARB -> 659 != 580
DISPATCH ERROR! glGetVertexAttribPointervARB -> 667 != 591
DISPATCH ERROR! glVertexAttrib4dARB -> 488 != 621
DISPATCH ERROR! glGetProgramLocalParameterdvARB -> 446 != 678
DISPATCH ERROR! glGetProgramivARB -> 449 != 680
DISPATCH ERROR! glVertexAttrib3sARB -> 478 != 619
DISPATCH ERROR! glProgramStringARB -> 461 != 667
DISPATCH ERROR! glProgramLocalParameter4fARB -> 459 != 674
DISPATCH ERROR! glEnableVertexAttribArrayARB -> 443 != 665
DISPATCH ERROR! glVertexAttrib4uivARB -> 496 != 658
DISPATCH ERROR! glBindProgramARB -> 658 != 579
DISPATCH ERROR! glVertexAttrib4svARB -> 494 != 626
DISPATCH ERROR! glVertexAttrib2svARB -> 473 != 614
DISPATCH ERROR! glVertexAttrib4NubvARB -> 484 != 628
DISPATCH ERROR! glGetProgramEnvParameterdvARB -> 444 != 676
DISPATCH ERROR! glVertexAttrib2sARB -> 472 != 613
DISPATCH ERROR! glVertexAttrib1fvARB -> 465 != 606
DISPATCH ERROR! glGenProgramsARB -> 661 != 582
DISPATCH ERROR! glWindowPos3f -> 634 != 523
DISPATCH ERROR! glWindowPos2dv -> 625 != 514
DISPATCH ERROR! glWindowPos2sv -> 631 != 520
DISPATCH ERROR! glWindowPos3d -> 632 != 521
DISPATCH ERROR! glWindowPos2fv -> 627 != 516
DISPATCH ERROR! glWindowPos2d -> 624 != 513
DISPATCH ERROR! glWindowPos3dv -> 633 != 522
DISPATCH ERROR! glWindowPos3fv -> 635 != 524
DISPATCH ERROR! glWindowPos2i -> 628 != 517
DISPATCH ERROR! glWindowPos3s -> 638 != 527
DISPATCH ERROR! glWindowPos2iv -> 629 != 518
DISPATCH ERROR! glWindowPos2s -> 630 != 519
DISPATCH ERROR! glWindowPos3i -> 636 != 525
DISPATCH ERROR! glWindowPos3iv -> 637 != 526
DISPATCH ERROR! glWindowPos3sv -> 639 != 528
DISPATCH ERROR! glWindowPos2f -> 626 != 515
DISPATCH ERROR! glBlendEquationSeparateEXT -> 749 != 710
DISPATCH ERROR! glBlendFuncSeparate -> 607 != 537
DISPATCH ERROR! glCullParameterdvEXT -> 580 != 542
DISPATCH ERROR! glCullParameterfvEXT -> 581 != 543
DISPATCH ERROR! glFogCoordd -> 602 != 547
DISPATCH ERROR! glFogCoordf -> 604 != 545
DISPATCH ERROR! glFogCoordPointer -> 601 != 549
DISPATCH ERROR! glFogCoordfv -> 605 != 546
DISPATCH ERROR! glFogCoorddv -> 603 != 548
DISPATCH ERROR! glMultiDrawElements -> 600 != 645
DISPATCH ERROR! glMultiDrawArrays -> 599 != 644
DISPATCH ERROR! glSecondaryColor3i -> 588 != 567
DISPATCH ERROR! glSecondaryColor3b -> 582 != 561
DISPATCH ERROR! glSecondaryColor3bv -> 583 != 562
DISPATCH ERROR! glSecondaryColor3s -> 590 != 569
DISPATCH ERROR! glSecondaryColor3d -> 584 != 563
DISPATCH ERROR! glSecondaryColorPointer -> 598 != 577
DISPATCH ERROR! glSecondaryColor3ui -> 594 != 573
DISPATCH ERROR! glSecondaryColor3usv -> 597 != 576
DISPATCH ERROR! glSecondaryColor3iv -> 589 != 568
DISPATCH ERROR! glSecondaryColor3fv -> 587 != 566
DISPATCH ERROR! glSecondaryColor3ubv -> 593 != 572
DISPATCH ERROR! glSecondaryColor3uiv -> 595 != 574
DISPATCH ERROR! glSecondaryColor3dv -> 585 != 564
DISPATCH ERROR! glSecondaryColor3us -> 596 != 575
DISPATCH ERROR! glSecondaryColor3ub -> 592 != 571
DISPATCH ERROR! glSecondaryColor3f -> 586 != 565
DISPATCH ERROR! glSecondaryColor3sv -> 591 != 570
DISPATCH ERROR! glProgramParameter4fNV -> 675 != 596
DISPATCH ERROR! glVertexAttrib4ubvNV -> 706 != 781
DISPATCH ERROR! glVertexAttrib4svNV -> 704 != 779
DISPATCH ERROR! glVertexAttribs1dvNV -> 708 != 629
DISPATCH ERROR! glProgramParameter4dvNV -> 674 != 595
DISPATCH ERROR! glVertexAttrib4fNV -> 701 != 776
DISPATCH ERROR! glVertexAttrib2dNV -> 687 != 762
DISPATCH ERROR! glVertexAttrib4ubNV -> 705 != 780
DISPATCH ERROR! glVertexAttribs3dvNV -> 714 != 635
DISPATCH ERROR! glVertexAttribs4fvNV -> 718 != 639
DISPATCH ERROR! glVertexAttrib2sNV -> 691 != 766
DISPATCH ERROR! glVertexAttribs3fvNV -> 715 != 636
DISPATCH ERROR! glProgramParameter4dNV -> 673 != 594
DISPATCH ERROR! glLoadProgramNV -> 672 != 593
DISPATCH ERROR! glVertexAttrib4fvNV -> 702 != 777
DISPATCH ERROR! glVertexAttrib3fNV -> 695 != 770
DISPATCH ERROR! glVertexAttribs2dvNV -> 711 != 632
DISPATCH ERROR! glGetProgramParameterfvNV -> 663 != 584
DISPATCH ERROR! glVertexAttrib3dNV -> 693 != 768
DISPATCH ERROR! glVertexAttrib2fvNV -> 690 != 765
DISPATCH ERROR! glVertexAttrib2dvNV -> 688 != 763
DISPATCH ERROR! glVertexAttrib1dvNV -> 682 != 757
DISPATCH ERROR! glProgramParameter4fvNV -> 676 != 597
DISPATCH ERROR! glVertexAttrib1svNV -> 686 != 761
DISPATCH ERROR! glVertexAttribs2svNV -> 713 != 634
DISPATCH ERROR! glGetVertexAttribivNV -> 670 != 755
DISPATCH ERROR! glGetVertexAttribfvNV -> 669 != 754
DISPATCH ERROR! glVertexAttrib2svNV -> 692 != 767
DISPATCH ERROR! glVertexAttribs1fvNV -> 709 != 630
DISPATCH ERROR! glIsProgramARB -> 671 != 592
DISPATCH ERROR! glVertexAttrib4sNV -> 703 != 778
DISPATCH ERROR! glVertexAttrib2fNV -> 689 != 764
DISPATCH ERROR! glRequestResidentProgramsNV -> 679 != 600
DISPATCH ERROR! glExecuteProgramNV -> 660 != 581
DISPATCH ERROR! glVertexAttribPointerNV -> 707 != 602
DISPATCH ERROR! glTrackMatrixNV -> 680 != 601
DISPATCH ERROR! glGetProgramParameterdvNV -> 662 != 583
DISPATCH ERROR! glVertexAttrib3sNV -> 697 != 772
DISPATCH ERROR! glGetTrackMatrixivNV -> 666 != 587
DISPATCH ERROR! glVertexAttrib3svNV -> 698 != 773
DISPATCH ERROR! glProgramParameters4fvNV -> 678 != 599
DISPATCH ERROR! glGetProgramivNV -> 665 != 585
DISPATCH ERROR! glGetVertexAttribdvNV -> 668 != 753
DISPATCH ERROR! glVertexAttrib3fvNV -> 696 != 771
DISPATCH ERROR! glVertexAttribs2fvNV -> 712 != 633
DISPATCH ERROR! glVertexAttrib1fvNV -> 684 != 759
DISPATCH ERROR! glDeleteProgramsARB -> 659 != 580
DISPATCH ERROR! glGetVertexAttribPointervARB -> 667 != 591
DISPATCH ERROR! glGetProgramStringNV -> 664 != 586
DISPATCH ERROR! glVertexAttribs4dvNV -> 717 != 638
DISPATCH ERROR! glProgramParameters4dvNV -> 677 != 598
DISPATCH ERROR! glVertexAttrib1fNV -> 683 != 758
DISPATCH ERROR! glVertexAttrib4dNV -> 699 != 774
DISPATCH ERROR! glVertexAttribs4ubvNV -> 720 != 641
DISPATCH ERROR! glVertexAttribs3svNV -> 716 != 637
DISPATCH ERROR! glVertexAttrib1sNV -> 685 != 760
DISPATCH ERROR! glBindProgramARB -> 658 != 579
DISPATCH ERROR! glAreProgramsResidentNV -> 657 != 578
DISPATCH ERROR! glVertexAttrib3dvNV -> 694 != 769
DISPATCH ERROR! glVertexAttrib1dNV -> 681 != 756
DISPATCH ERROR! glVertexAttribs4svNV -> 719 != 640
DISPATCH ERROR! glVertexAttribs1svNV -> 710 != 631
DISPATCH ERROR! glGenProgramsARB -> 661 != 582
DISPATCH ERROR! glVertexAttrib4dvNV -> 700 != 775
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x31
DISPATCH ERROR! glSampleCoverage -> 434 != 412
DISPATCH ERROR! glPointParameterf -> 576 != 458
DISPATCH ERROR! glPointParameterfv -> 577 != 459
DISPATCH ERROR! glCompressedTexSubImage2D -> 439 != 558
DISPATCH ERROR! glCompressedTexImage3D -> 437 != 554
DISPATCH ERROR! glCompressedTexImage1D -> 435 != 556
DISPATCH ERROR! glCompressedTexSubImage1D -> 438 != 559
DISPATCH ERROR! glCompressedTexSubImage3D -> 440 != 557
DISPATCH ERROR! glCompressedTexImage2D -> 436 != 555
DISPATCH ERROR! glGetCompressedTexImage -> 441 != 560
DISPATCH ERROR! glGetBufferSubData -> 506 != 695
DISPATCH ERROR! glBufferSubData -> 501 != 690
DISPATCH ERROR! glBufferData -> 500 != 689
DISPATCH ERROR! glGetBufferPointerv -> 505 != 694
DISPATCH ERROR! glGetBufferParameteriv -> 504 != 693
DISPATCH ERROR! glMapBuffer -> 508 != 697
DISPATCH ERROR! glIsBuffer -> 507 != 696
DISPATCH ERROR! glDeleteBuffers -> 502 != 691
DISPATCH ERROR! glUnmapBuffer -> 509 != 698
DISPATCH ERROR! glBindBuffer -> 499 != 688
DISPATCH ERROR! glGenBuffers -> 503 != 692
DISPATCH ERROR! glProgramEnvParameter4dvARB -> 454 != 669
DISPATCH ERROR! glVertexAttrib2fARB -> 470 != 611
DISPATCH ERROR! glVertexAttrib3fARB -> 476 != 617
DISPATCH ERROR! glVertexAttrib1svARB -> 467 != 608
DISPATCH ERROR! glVertexAttrib4NusvARB -> 486 != 662
DISPATCH ERROR! glDisableVertexAttribArrayARB -> 442 != 666
DISPATCH ERROR! glProgramLocalParameter4dARB -> 457 != 672
DISPATCH ERROR! glVertexAttrib1fARB -> 464 != 605
DISPATCH ERROR! glVertexAttrib4NbvARB -> 480 != 659
DISPATCH ERROR! glVertexAttrib1sARB -> 466 != 607
DISPATCH ERROR! glGetProgramLocalParameterfvARB -> 447 != 679
DISPATCH ERROR! glVertexAttrib3dvARB -> 475 != 616
DISPATCH ERROR! glProgramEnvParameter4fvARB -> 456 != 671
DISPATCH ERROR! glGetVertexAttribivARB -> 452 != 590
DISPATCH ERROR! glVertexAttrib4ivARB -> 492 != 655
DISPATCH ERROR! glVertexAttrib4bvARB -> 487 != 654
DISPATCH ERROR! glVertexAttrib3dARB -> 474 != 615
DISPATCH ERROR! glVertexAttrib4fARB -> 490 != 623
DISPATCH ERROR! glVertexAttrib4fvARB -> 491 != 624
DISPATCH ERROR! glProgramLocalParameter4dvARB -> 458 != 673
DISPATCH ERROR! glVertexAttrib4usvARB -> 497 != 657
DISPATCH ERROR! glVertexAttrib2dARB -> 468 != 609
DISPATCH ERROR! glVertexAttrib1dvARB -> 463 != 604
DISPATCH ERROR! glGetVertexAttribfvARB -> 451 != 589
DISPATCH ERROR! glVertexAttrib4ubvARB -> 495 != 656
DISPATCH ERROR! glProgramEnvParameter4fARB -> 455 != 670
DISPATCH ERROR! glVertexAttrib4sARB -> 493 != 625
DISPATCH ERROR! glVertexAttrib2dvARB -> 469 != 610
DISPATCH ERROR! glVertexAttrib2fvARB -> 471 != 612
DISPATCH ERROR! glVertexAttrib4NivARB -> 481 != 661
DISPATCH ERROR! glGetProgramStringARB -> 448 != 681
DISPATCH ERROR! glVertexAttrib4NuivARB -> 485 != 663
DISPATCH ERROR! glIsProgramARB -> 671 != 592
DISPATCH ERROR! glProgramEnvParameter4dARB -> 453 != 668
DISPATCH ERROR! glVertexAttrib1dARB -> 462 != 603
DISPATCH ERROR! glVertexAttrib3svARB -> 479 != 620
DISPATCH ERROR! glGetVertexAttribdvARB -> 450 != 588
DISPATCH ERROR! glVertexAttrib4dvARB -> 489 != 622
DISPATCH ERROR! glVertexAttribPointerARB -> 498 != 664
DISPATCH ERROR! glVertexAttrib4NsvARB -> 482 != 660
DISPATCH ERROR! glVertexAttrib3fvARB -> 477 != 618
DISPATCH ERROR! glVertexAttrib4NubARB -> 483 != 627
DISPATCH ERROR! glGetProgramEnvParameterfvARB -> 445 != 677
DISPATCH ERROR! glProgramLocalParameter4fvARB -> 460 != 675
DISPATCH ERROR! glDeleteProgramsARB -> 659 != 580
DISPATCH ERROR! glGetVertexAttribPointervARB -> 667 != 591
DISPATCH ERROR! glVertexAttrib4dARB -> 488 != 621
DISPATCH ERROR! glGetProgramLocalParameterdvARB -> 446 != 678
DISPATCH ERROR! glGetProgramivARB -> 449 != 680
DISPATCH ERROR! glVertexAttrib3sARB -> 478 != 619
DISPATCH ERROR! glProgramStringARB -> 461 != 667
DISPATCH ERROR! glProgramLocalParameter4fARB -> 459 != 674
DISPATCH ERROR! glEnableVertexAttribArrayARB -> 443 != 665
DISPATCH ERROR! glVertexAttrib4uivARB -> 496 != 658
DISPATCH ERROR! glBindProgramARB -> 658 != 579
DISPATCH ERROR! glVertexAttrib4svARB -> 494 != 626
DISPATCH ERROR! glVertexAttrib2svARB -> 473 != 614
DISPATCH ERROR! glVertexAttrib4NubvARB -> 484 != 628
DISPATCH ERROR! glGetProgramEnvParameterdvARB -> 444 != 676
DISPATCH ERROR! glVertexAttrib2sARB -> 472 != 613
DISPATCH ERROR! glVertexAttrib1fvARB -> 465 != 606
DISPATCH ERROR! glGenProgramsARB -> 661 != 582
DISPATCH ERROR! glWindowPos3f -> 634 != 523
DISPATCH ERROR! glWindowPos2dv -> 625 != 514
DISPATCH ERROR! glWindowPos2sv -> 631 != 520
DISPATCH ERROR! glWindowPos3d -> 632 != 521
DISPATCH ERROR! glWindowPos2fv -> 627 != 516
DISPATCH ERROR! glWindowPos2d -> 624 != 513
DISPATCH ERROR! glWindowPos3dv -> 633 != 522
DISPATCH ERROR! glWindowPos3fv -> 635 != 524
DISPATCH ERROR! glWindowPos2i -> 628 != 517
DISPATCH ERROR! glWindowPos3s -> 638 != 527
DISPATCH ERROR! glWindowPos2iv -> 629 != 518
DISPATCH ERROR! glWindowPos2s -> 630 != 519
DISPATCH ERROR! glWindowPos3i -> 636 != 525
DISPATCH ERROR! glWindowPos3iv -> 637 != 526
DISPATCH ERROR! glWindowPos3sv -> 639 != 528
DISPATCH ERROR! glWindowPos2f -> 626 != 515
DISPATCH ERROR! glBlendEquationSeparateEXT -> 749 != 710
DISPATCH ERROR! glBlendFuncSeparate -> 607 != 537
DISPATCH ERROR! glCullParameterdvEXT -> 580 != 542
DISPATCH ERROR! glCullParameterfvEXT -> 581 != 543
DISPATCH ERROR! glFogCoordd -> 602 != 547
DISPATCH ERROR! glFogCoordf -> 604 != 545
DISPATCH ERROR! glFogCoordPointer -> 601 != 549
DISPATCH ERROR! glFogCoordfv -> 605 != 546
DISPATCH ERROR! glFogCoorddv -> 603 != 548
DISPATCH ERROR! glMultiDrawElements -> 600 != 645
DISPATCH ERROR! glMultiDrawArrays -> 599 != 644
DISPATCH ERROR! glSecondaryColor3i -> 588 != 567
DISPATCH ERROR! glSecondaryColor3b -> 582 != 561
DISPATCH ERROR! glSecondaryColor3bv -> 583 != 562
DISPATCH ERROR! glSecondaryColor3s -> 590 != 569
DISPATCH ERROR! glSecondaryColor3d -> 584 != 563
DISPATCH ERROR! glSecondaryColorPointer -> 598 != 577
DISPATCH ERROR! glSecondaryColor3ui -> 594 != 573
DISPATCH ERROR! glSecondaryColor3usv -> 597 != 576
DISPATCH ERROR! glSecondaryColor3iv -> 589 != 568
DISPATCH ERROR! glSecondaryColor3fv -> 587 != 566
DISPATCH ERROR! glSecondaryColor3ubv -> 593 != 572
DISPATCH ERROR! glSecondaryColor3uiv -> 595 != 574
DISPATCH ERROR! glSecondaryColor3dv -> 585 != 564
DISPATCH ERROR! glSecondaryColor3us -> 596 != 575
DISPATCH ERROR! glSecondaryColor3ub -> 592 != 571
DISPATCH ERROR! glSecondaryColor3f -> 586 != 565
DISPATCH ERROR! glSecondaryColor3sv -> 591 != 570
DISPATCH ERROR! glProgramParameter4fNV -> 675 != 596
DISPATCH ERROR! glVertexAttrib4ubvNV -> 706 != 781
DISPATCH ERROR! glVertexAttrib4svNV -> 704 != 779
DISPATCH ERROR! glVertexAttribs1dvNV -> 708 != 629
DISPATCH ERROR! glProgramParameter4dvNV -> 674 != 595
DISPATCH ERROR! glVertexAttrib4fNV -> 701 != 776
DISPATCH ERROR! glVertexAttrib2dNV -> 687 != 762
DISPATCH ERROR! glVertexAttrib4ubNV -> 705 != 780
DISPATCH ERROR! glVertexAttribs3dvNV -> 714 != 635
DISPATCH ERROR! glVertexAttribs4fvNV -> 718 != 639
DISPATCH ERROR! glVertexAttrib2sNV -> 691 != 766
DISPATCH ERROR! glVertexAttribs3fvNV -> 715 != 636
DISPATCH ERROR! glProgramParameter4dNV -> 673 != 594
DISPATCH ERROR! glLoadProgramNV -> 672 != 593
DISPATCH ERROR! glVertexAttrib4fvNV -> 702 != 777
DISPATCH ERROR! glVertexAttrib3fNV -> 695 != 770
DISPATCH ERROR! glVertexAttribs2dvNV -> 711 != 632
DISPATCH ERROR! glGetProgramParameterfvNV -> 663 != 584
DISPATCH ERROR! glVertexAttrib3dNV -> 693 != 768
DISPATCH ERROR! glVertexAttrib2fvNV -> 690 != 765
DISPATCH ERROR! glVertexAttrib2dvNV -> 688 != 763
DISPATCH ERROR! glVertexAttrib1dvNV -> 682 != 757
DISPATCH ERROR! glProgramParameter4fvNV -> 676 != 597
DISPATCH ERROR! glVertexAttrib1svNV -> 686 != 761
DISPATCH ERROR! glVertexAttribs2svNV -> 713 != 634
DISPATCH ERROR! glGetVertexAttribivNV -> 670 != 755
DISPATCH ERROR! glGetVertexAttribfvNV -> 669 != 754
DISPATCH ERROR! glVertexAttrib2svNV -> 692 != 767
DISPATCH ERROR! glVertexAttribs1fvNV -> 709 != 630
DISPATCH ERROR! glIsProgramARB -> 671 != 592
DISPATCH ERROR! glVertexAttrib4sNV -> 703 != 778
DISPATCH ERROR! glVertexAttrib2fNV -> 689 != 764
DISPATCH ERROR! glRequestResidentProgramsNV -> 679 != 600
DISPATCH ERROR! glExecuteProgramNV -> 660 != 581
DISPATCH ERROR! glVertexAttribPointerNV -> 707 != 602
DISPATCH ERROR! glTrackMatrixNV -> 680 != 601
DISPATCH ERROR! glGetProgramParameterdvNV -> 662 != 583
DISPATCH ERROR! glVertexAttrib3sNV -> 697 != 772
DISPATCH ERROR! glGetTrackMatrixivNV -> 666 != 587
DISPATCH ERROR! glVertexAttrib3svNV -> 698 != 773
DISPATCH ERROR! glProgramParameters4fvNV -> 678 != 599
DISPATCH ERROR! glGetProgramivNV -> 665 != 585
DISPATCH ERROR! glGetVertexAttribdvNV -> 668 != 753
DISPATCH ERROR! glVertexAttrib3fvNV -> 696 != 771
DISPATCH ERROR! glVertexAttribs2fvNV -> 712 != 633
DISPATCH ERROR! glVertexAttrib1fvNV -> 684 != 759
DISPATCH ERROR! glDeleteProgramsARB -> 659 != 580
DISPATCH ERROR! glGetVertexAttribPointervARB -> 667 != 591
DISPATCH ERROR! glGetProgramStringNV -> 664 != 586
DISPATCH ERROR! glVertexAttribs4dvNV -> 717 != 638
DISPATCH ERROR! glProgramParameters4dvNV -> 677 != 598
DISPATCH ERROR! glVertexAttrib1fNV -> 683 != 758
DISPATCH ERROR! glVertexAttrib4dNV -> 699 != 774
DISPATCH ERROR! glVertexAttribs4ubvNV -> 720 != 641
DISPATCH ERROR! glVertexAttribs3svNV -> 716 != 637
DISPATCH ERROR! glVertexAttrib1sNV -> 685 != 760
DISPATCH ERROR! glBindProgramARB -> 658 != 579
DISPATCH ERROR! glAreProgramsResidentNV -> 657 != 578
DISPATCH ERROR! glVertexAttrib3dvNV -> 694 != 769
DISPATCH ERROR! glVertexAttrib1dNV -> 681 != 756
DISPATCH ERROR! glVertexAttribs4svNV -> 719 != 640
DISPATCH ERROR! glVertexAttribs1svNV -> 710 != 631
DISPATCH ERROR! glGenProgramsARB -> 661 != 582
DISPATCH ERROR! glVertexAttrib4dvNV -> 700 != 775


Don't understand why these dispatch errors show up. They don't show up when I use i810 driver instead of intel in xorg.conf. Although then copmiz stops working. 

Here's my xorg.conf:

> 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg


Section "Files"

        FontPath "/usr/share/X11/fonts/misc"
        FontPath "/usr/share/X11/fonts/cyrillic"
        FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath "/usr/share/X11/fonts/Type1"
        FontPath "/usr/share/X11/fonts/CID"
        FontPath "/usr/share/X11/fonts/100dpi"
        FontPath "/usr/share/X11/fonts/75dpi"
        FontPath "/usr/share/X11/fonts/truetype/"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "opengl"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbModel"      "pc101"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "on"
EndSection

Section "Extensions"
        Option         "Composite"   "Enable"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        VideoRam        10000
        Option          "XAANoOffscreenPixmaps" "true"
        Option          "DRI"     "true"
EndSection

Section "Monitor"
        Identifier      "LG 700E"
        HorizSync       30-71
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Monitor         "LG 700E"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           12
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           32
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        Option          "AIGLX" "true"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection



I've compiled DRI for intel and Mesa 3D drivers as well. 

Can anyone tell how to correct these errors?

Suggestions pls .. 

TIA

---


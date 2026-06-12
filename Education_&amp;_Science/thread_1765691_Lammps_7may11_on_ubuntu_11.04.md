---
title: "Lammps 7may11 on ubuntu 11.04"
date: 2011-05-23
forum: Education &amp; Science
---

### Post by shanisi on 2011-05-23
Dear All

Is there any easy way to install Lammps 7may11 on ubuntu 11.04.
I did a no. of tries but not succeed. I want to install it on single system. I have used to options mainly.  In  /opt/lammps-7May11/src# :

1. make serial
```

root@shanisi:/opt/lammps-7May11/src# make serial
make[1]: Entering directory `/opt/lammps-7May11/src/Obj_serial'
Makefile:103: angle_charmm.d: No such file or directory
Makefile:103: angle_class2.d: No such file or directory
Makefile:103: angle_cosine.d: No such file or directory
Makefile:103: angle_cosine_delta.d: No such file or directory
Makefile:103: angle_cosine_periodic.d: No such file or directory
Makefile:103: angle_cosine_squared.d: No such file or directory
Makefile:103: angle.d: No such file or directory
Makefile:103: angle_harmonic.d: No such file or directory
Makefile:103: angle_hybrid.d: No such file or directory
Makefile:103: angle_table.d: No such file or directory
Makefile:103: atom.d: No such file or directory
Makefile:103: atom_vec_angle.d: No such file or directory
Makefile:103: atom_vec_atomic.d: No such file or directory
Makefile:103: atom_vec_bond.d: No such file or directory
Makefile:103: atom_vec_charge.d: No such file or directory
Makefile:103: atom_vec.d: No such file or directory
Makefile:103: atom_vec_dipole.d: No such file or directory
Makefile:103: atom_vec_ellipsoid.d: No such file or directory
Makefile:103: atom_vec_full.d: No such file or directory
Makefile:103: atom_vec_hybrid.d: No such file or directory
Makefile:103: atom_vec_molecular.d: No such file or directory
Makefile:103: atom_vec_peri.d: No such file or directory
Makefile:103: atom_vec_sphere.d: No such file or directory
Makefile:103: bond_class2.d: No such file or directory
Makefile:103: bond.d: No such file or directory
Makefile:103: bond_fene.d: No such file or directory
Makefile:103: bond_fene_expand.d: No such file or directory
Makefile:103: bond_harmonic.d: No such file or directory
Makefile:103: bond_hybrid.d: No such file or directory
Makefile:103: bond_morse.d: No such file or directory
Makefile:103: bond_nonlinear.d: No such file or directory
Makefile:103: bond_quartic.d: No such file or directory
Makefile:103: bond_table.d: No such file or directory
Makefile:103: change_box.d: No such file or directory
Makefile:103: comm.d: No such file or directory
Makefile:103: compute_angle_local.d: No such file or directory
Makefile:103: compute_atom_molecule.d: No such file or directory
Makefile:103: compute_bond_local.d: No such file or directory
Makefile:103: compute_centro_atom.d: No such file or directory
Makefile:103: compute_cluster_atom.d: No such file or directory
Makefile:103: compute_cna_atom.d: No such file or directory
Makefile:103: compute_com.d: No such file or directory
Makefile:103: compute_com_molecule.d: No such file or directory
Makefile:103: compute_coord_atom.d: No such file or directory
Makefile:103: compute.d: No such file or directory
Makefile:103: compute_damage_atom.d: No such file or directory
Makefile:103: compute_dihedral_local.d: No such file or directory
Makefile:103: compute_displace_atom.d: No such file or directory
Makefile:103: compute_erotate_asphere.d: No such file or directory
Makefile:103: compute_erotate_sphere.d: No such file or directory
Makefile:103: compute_event_displace.d: No such file or directory
Makefile:103: compute_group_group.d: No such file or directory
Makefile:103: compute_gyration.d: No such file or directory
Makefile:103: compute_gyration_molecule.d: No such file or directory
Makefile:103: compute_heat_flux.d: No such file or directory
Makefile:103: compute_improper_local.d: No such file or directory
Makefile:103: compute_ke_atom.d: No such file or directory
Makefile:103: compute_ke.d: No such file or directory
Makefile:103: compute_msd.d: No such file or directory
Makefile:103: compute_msd_molecule.d: No such file or directory
Makefile:103: compute_pair.d: No such file or directory
Makefile:103: compute_pair_local.d: No such file or directory
Makefile:103: compute_pe_atom.d: No such file or directory
Makefile:103: compute_pe.d: No such file or directory
Makefile:103: compute_pressure.d: No such file or directory
Makefile:103: compute_property_atom.d: No such file or directory
Makefile:103: compute_property_local.d: No such file or directory
Makefile:103: compute_property_molecule.d: No such file or directory
Makefile:103: compute_rdf.d: No such file or directory
Makefile:103: compute_reduce.d: No such file or directory
Makefile:103: compute_reduce_region.d: No such file or directory
Makefile:103: compute_stress_atom.d: No such file or directory
Makefile:103: compute_temp_asphere.d: No such file or directory
Makefile:103: compute_temp_com.d: No such file or directory
Makefile:103: compute_temp.d: No such file or directory
Makefile:103: compute_temp_deform.d: No such file or directory
Makefile:103: compute_temp_partial.d: No such file or directory
Makefile:103: compute_temp_profile.d: No such file or directory
Makefile:103: compute_temp_ramp.d: No such file or directory
Makefile:103: compute_temp_region.d: No such file or directory
Makefile:103: compute_temp_sphere.d: No such file or directory
Makefile:103: compute_ti.d: No such file or directory
Makefile:103: create_atoms.d: No such file or directory
Makefile:103: create_box.d: No such file or directory
Makefile:103: delete_atoms.d: No such file or directory
Makefile:103: delete_bonds.d: No such file or directory
Makefile:103: dihedral_charmm.d: No such file or directory
Makefile:103: dihedral_class2.d: No such file or directory
Makefile:103: dihedral.d: No such file or directory
Makefile:103: dihedral_harmonic.d: No such file or directory
Makefile:103: dihedral_helix.d: No such file or directory
Makefile:103: dihedral_hybrid.d: No such file or directory
Makefile:103: dihedral_multi_harmonic.d: No such file or directory
Makefile:103: dihedral_opls.d: No such file or directory
Makefile:103: displace_atoms.d: No such file or directory
Makefile:103: displace_box.d: No such file or directory
Makefile:103: domain.d: No such file or directory
Makefile:103: dump_atom.d: No such file or directory
Makefile:103: dump_cfg.d: No such file or directory
Makefile:103: dump.d: No such file or directory
Makefile:103: dump_custom.d: No such file or directory
Makefile:103: dump_dcd.d: No such file or directory
Makefile:103: dump_local.d: No such file or directory
Makefile:103: dump_xtc.d: No such file or directory
Makefile:103: dump_xyz.d: No such file or directory
Makefile:103: error.d: No such file or directory
Makefile:103: ewald.d: No such file or directory
Makefile:103: fft3d.d: No such file or directory
Makefile:103: fft3d_wrap.d: No such file or directory
Makefile:103: finish.d: No such file or directory
Makefile:103: fix_adapt.d: No such file or directory
Makefile:103: fix_addforce.d: No such file or directory
Makefile:103: fix_ave_atom.d: No such file or directory
Makefile:103: fix_ave_correlate.d: No such file or directory
Makefile:103: fix_aveforce.d: No such file or directory
Makefile:103: fix_ave_histo.d: No such file or directory
Makefile:103: fix_ave_spatial.d: No such file or directory
Makefile:103: fix_ave_time.d: No such file or directory
Makefile:103: fix_bond_break.d: No such file or directory
Makefile:103: fix_bond_create.d: No such file or directory
Makefile:103: fix_bond_swap.d: No such file or directory
Makefile:103: fix_box_relax.d: No such file or directory
Makefile:103: fix.d: No such file or directory
Makefile:103: fix_deform.d: No such file or directory
Makefile:103: fix_deposit.d: No such file or directory
Makefile:103: fix_drag.d: No such file or directory
Makefile:103: fix_dt_reset.d: No such file or directory
Makefile:103: fix_efield.d: No such file or directory
Makefile:103: fix_enforce2d.d: No such file or directory
Makefile:103: fix_evaporate.d: No such file or directory
Makefile:103: fix_event.d: No such file or directory
Makefile:103: fix_event_prd.d: No such file or directory
Makefile:103: fix_event_tad.d: No such file or directory
Makefile:103: fix_external.d: No such file or directory
Makefile:103: fix_freeze.d: No such file or directory
Makefile:103: fix_gpu.d: No such file or directory
Makefile:103: fix_gravity.d: No such file or directory
Makefile:103: fix_heat.d: No such file or directory
Makefile:103: fix_indent.d: No such file or directory
Makefile:103: fix_langevin.d: No such file or directory
Makefile:103: fix_lineforce.d: No such file or directory
Makefile:103: fix_minimize.d: No such file or directory
Makefile:103: fix_momentum.d: No such file or directory
Makefile:103: fix_move.d: No such file or directory
Makefile:103: fix_msst.d: No such file or directory
Makefile:103: fix_neb.d: No such file or directory
Makefile:103: fix_nh_asphere.d: No such file or directory
Makefile:103: fix_nh.d: No such file or directory
Makefile:103: fix_nh_sphere.d: No such file or directory
Makefile:103: fix_nph_asphere.d: No such file or directory
Makefile:103: fix_nph.d: No such file or directory
Makefile:103: fix_nph_sphere.d: No such file or directory
Makefile:103: fix_npt_asphere.d: No such file or directory
Makefile:103: fix_npt.d: No such file or directory
Makefile:103: fix_npt_sphere.d: No such file or directory
Makefile:103: fix_nve_asphere.d: No such file or directory
Makefile:103: fix_nve.d: No such file or directory
Makefile:103: fix_nve_limit.d: No such file or directory
Makefile:103: fix_nve_noforce.d: No such file or directory
Makefile:103: fix_nve_sphere.d: No such file or directory
Makefile:103: fix_nvt_asphere.d: No such file or directory
Makefile:103: fix_nvt.d: No such file or directory
Makefile:103: fix_nvt_sllod.d: No such file or directory
Makefile:103: fix_nvt_sphere.d: No such file or directory
Makefile:103: fix_orient_fcc.d: No such file or directory
Makefile:103: fix_peri_neigh.d: No such file or directory
Makefile:103: fix_planeforce.d: No such file or directory
Makefile:103: fix_poems.d: No such file or directory
Makefile:103: fix_pour.d: No such file or directory
Makefile:103: fix_press_berendsen.d: No such file or directory
Makefile:103: fix_print.d: No such file or directory
Makefile:103: fix_qeq_comb.d: No such file or directory
Makefile:103: fix_read_restart.d: No such file or directory
Makefile:103: fix_reax_bonds.d: No such file or directory
Makefile:103: fix_recenter.d: No such file or directory
Makefile:103: fix_respa.d: No such file or directory
Makefile:103: fix_rigid.d: No such file or directory
Makefile:103: fix_rigid_nve.d: No such file or directory
Makefile:103: fix_rigid_nvt.d: No such file or directory
Makefile:103: fix_setforce.d: No such file or directory
Makefile:103: fix_shake.d: No such file or directory
Makefile:103: fix_shear_history.d: No such file or directory
Makefile:103: fix_spring.d: No such file or directory
Makefile:103: fix_spring_rg.d: No such file or directory
Makefile:103: fix_spring_self.d: No such file or directory
Makefile:103: fix_store_force.d: No such file or directory
Makefile:103: fix_store_state.d: No such file or directory
Makefile:103: fix_temp_berendsen.d: No such file or directory
Makefile:103: fix_temp_rescale.d: No such file or directory
Makefile:103: fix_thermal_conductivity.d: No such file or directory
Makefile:103: fix_tmd.d: No such file or directory
Makefile:103: fix_ttm.d: No such file or directory
Makefile:103: fix_viscosity.d: No such file or directory
Makefile:103: fix_viscous.d: No such file or directory
Makefile:103: fix_wall_colloid.d: No such file or directory
Makefile:103: fix_wall.d: No such file or directory
Makefile:103: fix_wall_gran.d: No such file or directory
Makefile:103: fix_wall_harmonic.d: No such file or directory
Makefile:103: fix_wall_lj126.d: No such file or directory
Makefile:103: fix_wall_lj93.d: No such file or directory
Makefile:103: fix_wall_reflect.d: No such file or directory
Makefile:103: fix_wall_region.d: No such file or directory
Makefile:103: force.d: No such file or directory
Makefile:103: group.d: No such file or directory
Makefile:103: improper_class2.d: No such file or directory
Makefile:103: improper.d: No such file or directory
Makefile:103: improper_cvff.d: No such file or directory
Makefile:103: improper_harmonic.d: No such file or directory
Makefile:103: improper_hybrid.d: No such file or directory
Makefile:103: improper_umbrella.d: No such file or directory
Makefile:103: input.d: No such file or directory
Makefile:103: integrate.d: No such file or directory
Makefile:103: irregular.d: No such file or directory
Makefile:103: kspace.d: No such file or directory
Makefile:103: lammps.d: No such file or directory
Makefile:103: lattice.d: No such file or directory
Makefile:103: library.d: No such file or directory
Makefile:103: main.d: No such file or directory
Makefile:103: math_extra.d: No such file or directory
Makefile:103: memory.d: No such file or directory
Makefile:103: min_cg.d: No such file or directory
Makefile:103: min.d: No such file or directory
Makefile:103: min_fire.d: No such file or directory
Makefile:103: min_hftn.d: No such file or directory
Makefile:103: minimize.d: No such file or directory
Makefile:103: min_linesearch.d: No such file or directory
Makefile:103: min_quickmin.d: No such file or directory
Makefile:103: min_sd.d: No such file or directory
Makefile:103: modify.d: No such file or directory
Makefile:103: neb.d: No such file or directory
Makefile:103: neigh_bond.d: No such file or directory
Makefile:103: neighbor.d: No such file or directory
Makefile:103: neigh_derive.d: No such file or directory
Makefile:103: neigh_full.d: No such file or directory
Makefile:103: neigh_gran.d: No such file or directory
Makefile:103: neigh_half_bin.d: No such file or directory
Makefile:103: neigh_half_multi.d: No such file or directory
Makefile:103: neigh_half_nsq.d: No such file or directory
Makefile:103: neigh_list.d: No such file or directory
Makefile:103: neigh_request.d: No such file or directory
Makefile:103: neigh_respa.d: No such file or directory
Makefile:103: neigh_stencil.d: No such file or directory
Makefile:103: output.d: No such file or directory
Makefile:103: pack.d: No such file or directory
Makefile:103: pair_airebo.d: No such file or directory
Makefile:103: pair_born_coul_long.d: No such file or directory
Makefile:103: pair_born.d: No such file or directory
Makefile:103: pair_buck_coul_cut.d: No such file or directory
Makefile:103: pair_buck_coul_long.d: No such file or directory
Makefile:103: pair_buck.d: No such file or directory
Makefile:103: pair_colloid.d: No such file or directory
Makefile:103: pair_comb.d: No such file or directory
Makefile:103: pair_coul_cut.d: No such file or directory
Makefile:103: pair_coul_debye.d: No such file or directory
Makefile:103: pair_coul_long.d: No such file or directory
Makefile:103: pair.d: No such file or directory
Makefile:103: pair_dipole_cut.d: No such file or directory
Makefile:103: pair_dpd.d: No such file or directory
Makefile:103: pair_dpd_tstat.d: No such file or directory
Makefile:103: pair_dsmc.d: No such file or directory
Makefile:103: pair_eam_alloy.d: No such file or directory
Makefile:103: pair_eam_alloy_opt.d: No such file or directory
Makefile:103: pair_eam.d: No such file or directory
Makefile:103: pair_eam_fs.d: No such file or directory
Makefile:103: pair_eam_fs_opt.d: No such file or directory
Makefile:103: pair_eam_opt.d: No such file or directory
Makefile:103: pair_eim.d: No such file or directory
Makefile:103: pair_gauss.d: No such file or directory
Makefile:103: pair_gayberne.d: No such file or directory
Makefile:103: pair_gayberne_gpu.d: No such file or directory
Makefile:103: pair_gran_hertz_history.d: No such file or directory
Makefile:103: pair_gran_hooke.d: No such file or directory
Makefile:103: pair_gran_hooke_history.d: No such file or directory
Makefile:103: pair_hbond_dreiding_lj.d: No such file or directory
Makefile:103: pair_hbond_dreiding_morse.d: No such file or directory
Makefile:103: pair_hybrid.d: No such file or directory
Makefile:103: pair_hybrid_overlay.d: No such file or directory
Makefile:103: pair_lj96_cut.d: No such file or directory
Makefile:103: pair_lj96_cut_gpu.d: No such file or directory
Makefile:103: pair_lj_charmm_coul_charmm.d: No such file or directory
Makefile:103: pair_lj_charmm_coul_charmm_implicit.d: No such file or directory
Makefile:103: pair_lj_charmm_coul_long.d: No such file or directory
Makefile:103: pair_lj_charmm_coul_long_gpu.d: No such file or directory
Makefile:103: pair_lj_charmm_coul_long_opt.d: No such file or directory
Makefile:103: pair_lj_class2_coul_cut.d: No such file or directory
Makefile:103: pair_lj_class2_coul_long.d: No such file or directory
Makefile:103: pair_lj_class2.d: No such file or directory
Makefile:103: pair_lj_cut_coul_cut.d: No such file or directory
Makefile:103: pair_lj_cut_coul_cut_gpu.d: No such file or directory
Makefile:103: pair_lj_cut_coul_debye.d: No such file or directory
Makefile:103: pair_lj_cut_coul_long.d: No such file or directory
Makefile:103: pair_lj_cut_coul_long_gpu.d: No such file or directory
Makefile:103: pair_lj_cut_coul_long_tip4p.d: No such file or directory
Makefile:103: pair_lj_cut.d: No such file or directory
Makefile:103: pair_lj_cut_gpu.d: No such file or directory
Makefile:103: pair_lj_cut_opt.d: No such file or directory
Makefile:103: pair_lj_expand.d: No such file or directory
Makefile:103: pair_lj_expand_gpu.d: No such file or directory
Makefile:103: pair_lj_gromacs_coul_gromacs.d: No such file or directory
Makefile:103: pair_lj_gromacs.d: No such file or directory
Makefile:103: pair_lj_smooth.d: No such file or directory
Makefile:103: pair_lubricate.d: No such file or directory
Makefile:103: pair_meam.d: No such file or directory
Makefile:103: pair_morse.d: No such file or directory
Makefile:103: pair_morse_gpu.d: No such file or directory
Makefile:103: pair_morse_opt.d: No such file or directory
Makefile:103: pair_peri_lps.d: No such file or directory
Makefile:103: pair_peri_pmb.d: No such file or directory
Makefile:103: pair_reax.d: No such file or directory
Makefile:103: pair_resquared.d: No such file or directory
Makefile:103: pair_soft.d: No such file or directory
Makefile:103: pair_sw.d: No such file or directory
Makefile:103: pair_table.d: No such file or directory
Makefile:103: pair_tersoff.d: No such file or directory
Makefile:103: pair_tersoff_zbl.d: No such file or directory
Makefile:103: pair_yukawa_colloid.d: No such file or directory
Makefile:103: pair_yukawa.d: No such file or directory
Makefile:103: pppm.d: No such file or directory
Makefile:103: pppm_gpu.d: No such file or directory
Makefile:103: pppm_gpu_double.d: No such file or directory
Makefile:103: pppm_gpu_single.d: No such file or directory
Makefile:103: pppm_tip4p.d: No such file or directory
Makefile:103: prd.d: No such file or directory
Makefile:103: random_mars.d: No such file or directory
Makefile:103: random_park.d: No such file or directory
Makefile:103: read_data.d: No such file or directory
Makefile:103: read_restart.d: No such file or directory
Makefile:103: region_block.d: No such file or directory
Makefile:103: region_cone.d: No such file or directory
Makefile:103: region.d: No such file or directory
Makefile:103: region_cylinder.d: No such file or directory
Makefile:103: region_intersect.d: No such file or directory
Makefile:103: region_plane.d: No such file or directory
Makefile:103: region_prism.d: No such file or directory
Makefile:103: region_sphere.d: No such file or directory
Makefile:103: region_union.d: No such file or directory
Makefile:103: remap.d: No such file or directory
Makefile:103: remap_wrap.d: No such file or directory
Makefile:103: replicate.d: No such file or directory
Makefile:103: respa.d: No such file or directory
Makefile:103: run.d: No such file or directory
Makefile:103: set.d: No such file or directory
Makefile:103: special.d: No such file or directory
Makefile:103: tad.d: No such file or directory
Makefile:103: temper.d: No such file or directory
Makefile:103: thermo.d: No such file or directory
Makefile:103: timer.d: No such file or directory
Makefile:103: universe.d: No such file or directory
Makefile:103: update.d: No such file or directory
Makefile:103: variable.d: No such file or directory
Makefile:103: velocity.d: No such file or directory
Makefile:103: verlet.d: No such file or directory
g++4 -O -DLAMMPS_GZIP -I../../lib/reax -I../../lib/poems -I../../lib/meam  -I../STUBS -DFFT_NONE  -M verlet.cpp > verlet.d
/bin/sh: g++4: not found
make[1]: *** [verlet.d] Error 127
make[1]: Leaving directory `/opt/lammps-7May11/src/Obj_serial'
make: *** [serial] Error 2
root@shanisi:/opt/lammps-7May11/src# root@shanisi:/opt/lammps-7May11/src#


2. make linux

root@shanisi:/opt/lammps-7May11/src# make linux
make[1]: Entering directory `/opt/lammps-7May11/src/Obj_linux'
Makefile:104: angle_charmm.d: No such file or directory
Makefile:104: angle_class2.d: No such file or directory
Makefile:104: angle_cosine.d: No such file or directory
Makefile:104: angle_cosine_delta.d: No such file or directory
Makefile:104: angle_cosine_periodic.d: No such file or directory
Makefile:104: angle_cosine_squared.d: No such file or directory
Makefile:104: angle.d: No such file or directory
Makefile:104: angle_harmonic.d: No such file or directory
Makefile:104: angle_hybrid.d: No such file or directory
Makefile:104: angle_table.d: No such file or directory
Makefile:104: atom.d: No such file or directory
Makefile:104: atom_vec_angle.d: No such file or directory
Makefile:104: atom_vec_atomic.d: No such file or directory
Makefile:104: atom_vec_bond.d: No such file or directory
Makefile:104: atom_vec_charge.d: No such file or directory
Makefile:104: atom_vec.d: No such file or directory
Makefile:104: atom_vec_dipole.d: No such file or directory
Makefile:104: atom_vec_ellipsoid.d: No such file or directory
Makefile:104: atom_vec_full.d: No such file or directory
Makefile:104: atom_vec_hybrid.d: No such file or directory
Makefile:104: atom_vec_molecular.d: No such file or directory
Makefile:104: atom_vec_peri.d: No such file or directory
Makefile:104: atom_vec_sphere.d: No such file or directory
Makefile:104: bond_class2.d: No such file or directory
Makefile:104: bond.d: No such file or directory
Makefile:104: bond_fene.d: No such file or directory
Makefile:104: bond_fene_expand.d: No such file or directory
Makefile:104: bond_harmonic.d: No such file or directory
Makefile:104: bond_hybrid.d: No such file or directory
Makefile:104: bond_morse.d: No such file or directory
Makefile:104: bond_nonlinear.d: No such file or directory
Makefile:104: bond_quartic.d: No such file or directory
Makefile:104: bond_table.d: No such file or directory
Makefile:104: change_box.d: No such file or directory
Makefile:104: comm.d: No such file or directory
Makefile:104: compute_angle_local.d: No such file or directory
Makefile:104: compute_atom_molecule.d: No such file or directory
Makefile:104: compute_bond_local.d: No such file or directory
Makefile:104: compute_centro_atom.d: No such file or directory
Makefile:104: compute_cluster_atom.d: No such file or directory
Makefile:104: compute_cna_atom.d: No such file or directory
Makefile:104: compute_com.d: No such file or directory
Makefile:104: compute_com_molecule.d: No such file or directory
Makefile:104: compute_coord_atom.d: No such file or directory
Makefile:104: compute.d: No such file or directory
Makefile:104: compute_damage_atom.d: No such file or directory
Makefile:104: compute_dihedral_local.d: No such file or directory
Makefile:104: compute_displace_atom.d: No such file or directory
Makefile:104: compute_erotate_asphere.d: No such file or directory
Makefile:104: compute_erotate_sphere.d: No such file or directory
Makefile:104: compute_event_displace.d: No such file or directory
Makefile:104: compute_group_group.d: No such file or directory
Makefile:104: compute_gyration.d: No such file or directory
Makefile:104: compute_gyration_molecule.d: No such file or directory
Makefile:104: compute_heat_flux.d: No such file or directory
Makefile:104: compute_improper_local.d: No such file or directory
Makefile:104: compute_ke_atom.d: No such file or directory
Makefile:104: compute_ke.d: No such file or directory
Makefile:104: compute_msd.d: No such file or directory
Makefile:104: compute_msd_molecule.d: No such file or directory
Makefile:104: compute_pair.d: No such file or directory
Makefile:104: compute_pair_local.d: No such file or directory
Makefile:104: compute_pe_atom.d: No such file or directory
Makefile:104: compute_pe.d: No such file or directory
Makefile:104: compute_pressure.d: No such file or directory
Makefile:104: compute_property_atom.d: No such file or directory
Makefile:104: compute_property_local.d: No such file or directory
Makefile:104: compute_property_molecule.d: No such file or directory
Makefile:104: compute_rdf.d: No such file or directory
Makefile:104: compute_reduce.d: No such file or directory
Makefile:104: compute_reduce_region.d: No such file or directory
Makefile:104: compute_stress_atom.d: No such file or directory
Makefile:104: compute_temp_asphere.d: No such file or directory
Makefile:104: compute_temp_com.d: No such file or directory
Makefile:104: compute_temp.d: No such file or directory
Makefile:104: compute_temp_deform.d: No such file or directory
Makefile:104: compute_temp_partial.d: No such file or directory
Makefile:104: compute_temp_profile.d: No such file or directory
Makefile:104: compute_temp_ramp.d: No such file or directory
Makefile:104: compute_temp_region.d: No such file or directory
Makefile:104: compute_temp_sphere.d: No such file or directory
Makefile:104: compute_ti.d: No such file or directory
Makefile:104: create_atoms.d: No such file or directory
Makefile:104: create_box.d: No such file or directory
Makefile:104: delete_atoms.d: No such file or directory
Makefile:104: delete_bonds.d: No such file or directory
Makefile:104: dihedral_charmm.d: No such file or directory
Makefile:104: dihedral_class2.d: No such file or directory
Makefile:104: dihedral.d: No such file or directory
Makefile:104: dihedral_harmonic.d: No such file or directory
Makefile:104: dihedral_helix.d: No such file or directory
Makefile:104: dihedral_hybrid.d: No such file or directory
Makefile:104: dihedral_multi_harmonic.d: No such file or directory
Makefile:104: dihedral_opls.d: No such file or directory
Makefile:104: displace_atoms.d: No such file or directory
Makefile:104: displace_box.d: No such file or directory
Makefile:104: domain.d: No such file or directory
Makefile:104: dump_atom.d: No such file or directory
Makefile:104: dump_cfg.d: No such file or directory
Makefile:104: dump.d: No such file or directory
Makefile:104: dump_custom.d: No such file or directory
Makefile:104: dump_dcd.d: No such file or directory
Makefile:104: dump_local.d: No such file or directory
Makefile:104: dump_xtc.d: No such file or directory
Makefile:104: dump_xyz.d: No such file or directory
Makefile:104: error.d: No such file or directory
Makefile:104: ewald.d: No such file or directory
Makefile:104: fft3d.d: No such file or directory
Makefile:104: fft3d_wrap.d: No such file or directory
Makefile:104: finish.d: No such file or directory
Makefile:104: fix_adapt.d: No such file or directory
Makefile:104: fix_addforce.d: No such file or directory
Makefile:104: fix_ave_atom.d: No such file or directory
Makefile:104: fix_ave_correlate.d: No such file or directory
Makefile:104: fix_aveforce.d: No such file or directory
Makefile:104: fix_ave_histo.d: No such file or directory
Makefile:104: fix_ave_spatial.d: No such file or directory
Makefile:104: fix_ave_time.d: No such file or directory
Makefile:104: fix_bond_break.d: No such file or directory
Makefile:104: fix_bond_create.d: No such file or directory
Makefile:104: fix_bond_swap.d: No such file or directory
Makefile:104: fix_box_relax.d: No such file or directory
Makefile:104: fix.d: No such file or directory
Makefile:104: fix_deform.d: No such file or directory
Makefile:104: fix_deposit.d: No such file or directory
Makefile:104: fix_drag.d: No such file or directory
Makefile:104: fix_dt_reset.d: No such file or directory
Makefile:104: fix_efield.d: No such file or directory
Makefile:104: fix_enforce2d.d: No such file or directory
Makefile:104: fix_evaporate.d: No such file or directory
Makefile:104: fix_event.d: No such file or directory
Makefile:104: fix_event_prd.d: No such file or directory
Makefile:104: fix_event_tad.d: No such file or directory
Makefile:104: fix_external.d: No such file or directory
Makefile:104: fix_freeze.d: No such file or directory
Makefile:104: fix_gpu.d: No such file or directory
Makefile:104: fix_gravity.d: No such file or directory
Makefile:104: fix_heat.d: No such file or directory
Makefile:104: fix_indent.d: No such file or directory
Makefile:104: fix_langevin.d: No such file or directory
Makefile:104: fix_lineforce.d: No such file or directory
Makefile:104: fix_minimize.d: No such file or directory
Makefile:104: fix_momentum.d: No such file or directory
Makefile:104: fix_move.d: No such file or directory
Makefile:104: fix_msst.d: No such file or directory
Makefile:104: fix_neb.d: No such file or directory
Makefile:104: fix_nh_asphere.d: No such file or directory
Makefile:104: fix_nh.d: No such file or directory
Makefile:104: fix_nh_sphere.d: No such file or directory
Makefile:104: fix_nph_asphere.d: No such file or directory
Makefile:104: fix_nph.d: No such file or directory
Makefile:104: fix_nph_sphere.d: No such file or directory
Makefile:104: fix_npt_asphere.d: No such file or directory
Makefile:104: fix_npt.d: No such file or directory
Makefile:104: fix_npt_sphere.d: No such file or directory
Makefile:104: fix_nve_asphere.d: No such file or directory
Makefile:104: fix_nve.d: No such file or directory
Makefile:104: fix_nve_limit.d: No such file or directory
Makefile:104: fix_nve_noforce.d: No such file or directory
Makefile:104: fix_nve_sphere.d: No such file or directory
Makefile:104: fix_nvt_asphere.d: No such file or directory
Makefile:104: fix_nvt.d: No such file or directory
Makefile:104: fix_nvt_sllod.d: No such file or directory
Makefile:104: fix_nvt_sphere.d: No such file or directory
Makefile:104: fix_orient_fcc.d: No such file or directory
Makefile:104: fix_peri_neigh.d: No such file or directory
Makefile:104: fix_planeforce.d: No such file or directory
Makefile:104: fix_poems.d: No such file or directory
Makefile:104: fix_pour.d: No such file or directory
Makefile:104: fix_press_berendsen.d: No such file or directory
Makefile:104: fix_print.d: No such file or directory
Makefile:104: fix_qeq_comb.d: No such file or directory
Makefile:104: fix_read_restart.d: No such file or directory
Makefile:104: fix_reax_bonds.d: No such file or directory
Makefile:104: fix_recenter.d: No such file or directory
Makefile:104: fix_respa.d: No such file or directory
Makefile:104: fix_rigid.d: No such file or directory
Makefile:104: fix_rigid_nve.d: No such file or directory
Makefile:104: fix_rigid_nvt.d: No such file or directory
Makefile:104: fix_setforce.d: No such file or directory
Makefile:104: fix_shake.d: No such file or directory
Makefile:104: fix_shear_history.d: No such file or directory
Makefile:104: fix_spring.d: No such file or directory
Makefile:104: fix_spring_rg.d: No such file or directory
Makefile:104: fix_spring_self.d: No such file or directory
Makefile:104: fix_store_force.d: No such file or directory
Makefile:104: fix_store_state.d: No such file or directory
Makefile:104: fix_temp_berendsen.d: No such file or directory
Makefile:104: fix_temp_rescale.d: No such file or directory
Makefile:104: fix_thermal_conductivity.d: No such file or directory
Makefile:104: fix_tmd.d: No such file or directory
Makefile:104: fix_ttm.d: No such file or directory
Makefile:104: fix_viscosity.d: No such file or directory
Makefile:104: fix_viscous.d: No such file or directory
Makefile:104: fix_wall_colloid.d: No such file or directory
Makefile:104: fix_wall.d: No such file or directory
Makefile:104: fix_wall_gran.d: No such file or directory
Makefile:104: fix_wall_harmonic.d: No such file or directory
Makefile:104: fix_wall_lj126.d: No such file or directory
Makefile:104: fix_wall_lj93.d: No such file or directory
Makefile:104: fix_wall_reflect.d: No such file or directory
Makefile:104: fix_wall_region.d: No such file or directory
Makefile:104: force.d: No such file or directory
Makefile:104: group.d: No such file or directory
Makefile:104: improper_class2.d: No such file or directory
Makefile:104: improper.d: No such file or directory
Makefile:104: improper_cvff.d: No such file or directory
Makefile:104: improper_harmonic.d: No such file or directory
Makefile:104: improper_hybrid.d: No such file or directory
Makefile:104: improper_umbrella.d: No such file or directory
Makefile:104: input.d: No such file or directory
Makefile:104: integrate.d: No such file or directory
Makefile:104: irregular.d: No such file or directory
Makefile:104: kspace.d: No such file or directory
Makefile:104: lammps.d: No such file or directory
Makefile:104: lattice.d: No such file or directory
Makefile:104: library.d: No such file or directory
Makefile:104: main.d: No such file or directory
Makefile:104: math_extra.d: No such file or directory
Makefile:104: memory.d: No such file or directory
Makefile:104: min_cg.d: No such file or directory
Makefile:104: min.d: No such file or directory
Makefile:104: min_fire.d: No such file or directory
Makefile:104: min_hftn.d: No such file or directory
Makefile:104: minimize.d: No such file or directory
Makefile:104: min_linesearch.d: No such file or directory
Makefile:104: min_quickmin.d: No such file or directory
Makefile:104: min_sd.d: No such file or directory
Makefile:104: modify.d: No such file or directory
Makefile:104: neb.d: No such file or directory
Makefile:104: neigh_bond.d: No such file or directory
Makefile:104: neighbor.d: No such file or directory
Makefile:104: neigh_derive.d: No such file or directory
Makefile:104: neigh_full.d: No such file or directory
Makefile:104: neigh_gran.d: No such file or directory
Makefile:104: neigh_half_bin.d: No such file or directory
Makefile:104: neigh_half_multi.d: No such file or directory
Makefile:104: neigh_half_nsq.d: No such file or directory
Makefile:104: neigh_list.d: No such file or directory
Makefile:104: neigh_request.d: No such file or directory
Makefile:104: neigh_respa.d: No such file or directory
Makefile:104: neigh_stencil.d: No such file or directory
Makefile:104: output.d: No such file or directory
Makefile:104: pack.d: No such file or directory
Makefile:104: pair_airebo.d: No such file or directory
Makefile:104: pair_born_coul_long.d: No such file or directory
Makefile:104: pair_born.d: No such file or directory
Makefile:104: pair_buck_coul_cut.d: No such file or directory
Makefile:104: pair_buck_coul_long.d: No such file or directory
Makefile:104: pair_buck.d: No such file or directory
Makefile:104: pair_colloid.d: No such file or directory
Makefile:104: pair_comb.d: No such file or directory
Makefile:104: pair_coul_cut.d: No such file or directory
Makefile:104: pair_coul_debye.d: No such file or directory
Makefile:104: pair_coul_long.d: No such file or directory
Makefile:104: pair.d: No such file or directory
Makefile:104: pair_dipole_cut.d: No such file or directory
Makefile:104: pair_dpd.d: No such file or directory
Makefile:104: pair_dpd_tstat.d: No such file or directory
Makefile:104: pair_dsmc.d: No such file or directory
Makefile:104: pair_eam_alloy.d: No such file or directory
Makefile:104: pair_eam_alloy_opt.d: No such file or directory
Makefile:104: pair_eam.d: No such file or directory
Makefile:104: pair_eam_fs.d: No such file or directory
Makefile:104: pair_eam_fs_opt.d: No such file or directory
Makefile:104: pair_eam_opt.d: No such file or directory
Makefile:104: pair_eim.d: No such file or directory
Makefile:104: pair_gauss.d: No such file or directory
Makefile:104: pair_gayberne.d: No such file or directory
Makefile:104: pair_gayberne_gpu.d: No such file or directory
Makefile:104: pair_gran_hertz_history.d: No such file or directory
Makefile:104: pair_gran_hooke.d: No such file or directory
Makefile:104: pair_gran_hooke_history.d: No such file or directory
Makefile:104: pair_hbond_dreiding_lj.d: No such file or directory
Makefile:104: pair_hbond_dreiding_morse.d: No such file or directory
Makefile:104: pair_hybrid.d: No such file or directory
Makefile:104: pair_hybrid_overlay.d: No such file or directory
Makefile:104: pair_lj96_cut.d: No such file or directory
Makefile:104: pair_lj96_cut_gpu.d: No such file or directory
Makefile:104: pair_lj_charmm_coul_charmm.d: No such file or directory
Makefile:104: pair_lj_charmm_coul_charmm_implicit.d: No such file or directory
Makefile:104: pair_lj_charmm_coul_long.d: No such file or directory
Makefile:104: pair_lj_charmm_coul_long_gpu.d: No such file or directory
Makefile:104: pair_lj_charmm_coul_long_opt.d: No such file or directory
Makefile:104: pair_lj_class2_coul_cut.d: No such file or directory
Makefile:104: pair_lj_class2_coul_long.d: No such file or directory
Makefile:104: pair_lj_class2.d: No such file or directory
Makefile:104: pair_lj_cut_coul_cut.d: No such file or directory
Makefile:104: pair_lj_cut_coul_cut_gpu.d: No such file or directory
Makefile:104: pair_lj_cut_coul_debye.d: No such file or directory
Makefile:104: pair_lj_cut_coul_long.d: No such file or directory
Makefile:104: pair_lj_cut_coul_long_gpu.d: No such file or directory
Makefile:104: pair_lj_cut_coul_long_tip4p.d: No such file or directory
Makefile:104: pair_lj_cut.d: No such file or directory
Makefile:104: pair_lj_cut_gpu.d: No such file or directory
Makefile:104: pair_lj_cut_opt.d: No such file or directory
Makefile:104: pair_lj_expand.d: No such file or directory
Makefile:104: pair_lj_expand_gpu.d: No such file or directory
Makefile:104: pair_lj_gromacs_coul_gromacs.d: No such file or directory
Makefile:104: pair_lj_gromacs.d: No such file or directory
Makefile:104: pair_lj_smooth.d: No such file or directory
Makefile:104: pair_lubricate.d: No such file or directory
Makefile:104: pair_meam.d: No such file or directory
Makefile:104: pair_morse.d: No such file or directory
Makefile:104: pair_morse_gpu.d: No such file or directory
Makefile:104: pair_morse_opt.d: No such file or directory
Makefile:104: pair_peri_lps.d: No such file or directory
Makefile:104: pair_peri_pmb.d: No such file or directory
Makefile:104: pair_reax.d: No such file or directory
Makefile:104: pair_resquared.d: No such file or directory
Makefile:104: pair_soft.d: No such file or directory
Makefile:104: pair_sw.d: No such file or directory
Makefile:104: pair_table.d: No such file or directory
Makefile:104: pair_tersoff.d: No such file or directory
Makefile:104: pair_tersoff_zbl.d: No such file or directory
Makefile:104: pair_yukawa_colloid.d: No such file or directory
Makefile:104: pair_yukawa.d: No such file or directory
Makefile:104: pppm.d: No such file or directory
Makefile:104: pppm_gpu.d: No such file or directory
Makefile:104: pppm_gpu_double.d: No such file or directory
Makefile:104: pppm_gpu_single.d: No such file or directory
Makefile:104: pppm_tip4p.d: No such file or directory
Makefile:104: prd.d: No such file or directory
Makefile:104: random_mars.d: No such file or directory
Makefile:104: random_park.d: No such file or directory
Makefile:104: read_data.d: No such file or directory
Makefile:104: read_restart.d: No such file or directory
Makefile:104: region_block.d: No such file or directory
Makefile:104: region_cone.d: No such file or directory
Makefile:104: region.d: No such file or directory
Makefile:104: region_cylinder.d: No such file or directory
Makefile:104: region_intersect.d: No such file or directory
Makefile:104: region_plane.d: No such file or directory
Makefile:104: region_prism.d: No such file or directory
Makefile:104: region_sphere.d: No such file or directory
Makefile:104: region_union.d: No such file or directory
Makefile:104: remap.d: No such file or directory
Makefile:104: remap_wrap.d: No such file or directory
Makefile:104: replicate.d: No such file or directory
Makefile:104: respa.d: No such file or directory
Makefile:104: run.d: No such file or directory
Makefile:104: set.d: No such file or directory
Makefile:104: special.d: No such file or directory
Makefile:104: tad.d: No such file or directory
Makefile:104: temper.d: No such file or directory
Makefile:104: thermo.d: No such file or directory
Makefile:104: timer.d: No such file or directory
Makefile:104: universe.d: No such file or directory
Makefile:104: update.d: No such file or directory
mpiicc -O -DLAMMPS_GZIP -I../../lib/reax -I../../lib/poems -I../../lib/meam  -DMPICH_SKIP_MPICXX  -I/usr/local/fft     -DFFT_FFTW  -M update.cpp > update.d
/bin/sh: mpiicc: not found
make[1]: *** [update.d] Error 127
make[1]: Leaving directory `/opt/lammps-7May11/src/Obj_linux'
make: *** [linux] Error 2
root@shanisi:/opt/lammps-7May11/src#
```

---

### Post by rosencrantz on 2011-05-24
All the .d error messages are irrelevant. Your problem is that the makefile specifies the wrong compiler.
For the serial install, in src/MAKE/Makefile.serial replace all instances of g++4 with g++
If you want multithreading support and fftw, as supported by the linux install, make sure you have the following packages installed:
build-essential mpich-bin libmpich1.0-dev fftw2 fftw-dev libxaw7-dev 
(cf here: [http://katter-world.blogspot.com/2010/05/install-lammps-on-ubuntu.html](http://katter-world.blogspot.com/2010/05/install-lammps-on-ubuntu.html))
In Makefile.linux, change all instances of the icc compiler to mpic++ and specify the mpi include directories by adding the -I and -L compiler flags:
MPI_INC =       -DMPICH_SKIP_MPICXX -I/usr/lib/mpich/include/
MPI_PATH =      -L/usr/lib/mpich/lib/ 
(that's for my system, you can check the library and include directories with dpkg -L libmpich1.0-dev)
Props go to my office mate for helping me with my install.

---

### Post by Pand5461 on 2011-05-26
Shanisi, do you want to compile LAMMPS without parallel support? If so, use Makefile.serial (and yes, change g++4 to g++). You should also compile a dummy mpi lib in src/STUBS. I attach the file I used on my machine.

---

### Post by lammps on 2011-06-11
> **Pand5461 said:**
> Shanisi, do you want to compile LAMMPS without parallel support? If so, use Makefile.serial (and yes, change g++4 to g++). You should also compile a dummy mpi lib in src/STUBS. I attach the file I used on my machine.

I am having the same .d errors similar to Shanisi's post. I did edit my makefile.g++ in those g++4 places to g++. 

Also I added path to MPI lines as follows

[I]MPI_INC =       -DMPICH_SKIP_MPICXX -I/usr/lib/mpich/include
MPI_PATH =      -I/usr/lib/openmpi/include/mpi.h -L/usr/lib/mpich/lib
MPI_LIB =       -lmpich -lpthread[/I]

The compilation log for g++ is below. Error 127 shows different lines after each execution such as region_plane.d, region_intersect.d, region_cylinder.d


Any suggestions please.

[I]Makefile:108: region_cone.d: No such file or directory
Makefile:108: region_cylinder.d: No such file or directory
Makefile:108: region_intersect.d: No such file or directory
Makefile:108: region_plane.d: No such file or directory
g++ -g -O -DFFT_NONE -DUNIX  -DFFT_CUFFT -DCUDA_PRECISION=2 -DCUDA_ARCH=20  -I/usr/local/cuda/include  -DLAMMPS_GZIP -DLAMMPS_JPEG -I../../lib/cuda -DLMP_USER_CUDA -I../../lib/atc -I../../lib/reax -I../../lib/poems -I../../lib/meam  -DMPICH_SKIP_MPICXX -I/usr/lib/mpich/include -DFFT_FFTW   -I/usr/local/cuda/include      -M region_plane.cpp > region_plane.d
/bin/sh: g++: not found
make[1]: *** [region_plane.d] Error 127
make[1]: Leaving directory `/home/james/lammps-12Jun11/src/Obj_g++'
make: *** [g++] Error 2
[/I]

---


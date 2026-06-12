---
title: "dd maximal block size"
date: 2009-02-19
forum: General Help
---

### Post by kerneldaemon on 2009-02-19
Hello,

I'm using an ATA IDE drive. I wonder how can I specify the maximum block size to dd in order to speed things up a little bit.

```
 dd if=/dev/hda1 bs=? > /dev/null 
```

my hard drive sectors size is 512. Does bs need to be a multiple of it ?

thanks

---

### Post by snova on 2009-02-19
> **kerneldaemon said:**
> my hard drive sectors size is 512. Does bs need to be a multiple of it ?

Well, it doesn't *need* to be- it can be anything- but I think it's a lot more efficient.

Say, 1024, or 4096, or even larger...

---

### Post by dcstar on 2009-02-19
> **snova said:**
> Well, it doesn't *need* to be- it can be anything- but I think it's a lot more efficient.

Say, 1024, or 4096, or even larger...

When you do a partition copy in Gparted, it uses dd and does a throughput test beforehand to determine optimal block size.

Anyone using dd may want to use Gparted to find this value out for their particular system (you have to expand the details of the operation to see it).

---

### Post by kerneldaemon on 2009-02-20
I just took a look at the Gparted svn repository [http://svn.gnome.org/viewvc/gparted/trunk/src/GParted_Core.cc?revision=1071&view=markup]("http://svn.gnome.org/viewvc/gparted/trunk/src/GParted_Core.cc?revision=1071&view=markup")

In its final version, it no longer uses dd. It rather use its own algorithm. Here is how it looks like:
```
1839 	bool GParted_Core::copy_filesystem( const Glib::ustring & src_device,
1840 	const Glib::ustring & dst_device,
1841 	Sector src_start,
1842 	Sector dst_start,
1843 	Sector length,
1844 	OperationDetail & operationdetail,
1845 	bool readonly,
1846 	Sector & total_done )
1847 	{
1848 	operationdetail .add_child( OperationDetail( _("using internal algorithm"), STATUS_NONE ) ) ;
1849 	operationdetail .add_child( OperationDetail(
1850 	String::ucompose( readonly ? _("read %1 sectors") : _("copy %1 sectors"), length ), STATUS_NONE ) ) ;
1851 	
1852 	operationdetail .add_child( OperationDetail( _("finding optimal blocksize"), STATUS_NONE ) ) ;
1853 	
1854 	Sector benchmark_blocksize = readonly ? 128 : 64, N = 65536 ;
1855 	Sector optimal_blocksize = benchmark_blocksize ;
1856 	Sector offset_read = src_start,
1857 	offset_write = dst_start ;
1858 	
1859 	if ( dst_start > src_start )
1860 	{
1861 	offset_read += (length -N) ;
1862 	offset_write += (length -N) ;
1863 	}
1864 	
1865 	total_done = 0 ;
1866 	Sector done = 0 ;
1867 	Glib::Timer timer ;
1868 	double smallest_time = 1000000 ;
1869 	bool succes = true ;
1870 	
1871 	//Benchmark copy times using different block sizes to determine optimal size
1872 	while ( succes &&
1873 	llabs( done ) + N <= length &&
1874 	benchmark_blocksize <= N )
1875 	{
1876 	timer .reset() ;
1877 	succes = copy_blocks( src_device,
1878 	dst_device,
1879 	offset_read + done,
1880 	offset_write + done,
1881 	N,
1882 	benchmark_blocksize,
1883 	operationdetail .get_last_child(),
1884 	readonly,
1885 	total_done ) ;
1886 	timer.stop() ;
1887 	
1888 	operationdetail .get_last_child() .get_last_child() .add_child( OperationDetail(
1889 	String::ucompose( _("%1 seconds"), timer .elapsed() ), STATUS_NONE, FONT_ITALIC ) ) ;
1890 	
1891 	if ( timer .elapsed() <= smallest_time )
1892 	{
1893 	smallest_time = timer .elapsed() ;
1894 	optimal_blocksize = benchmark_blocksize ;
1895 	}
1896 	benchmark_blocksize *= 2 ;
1897 	
1898 	if ( ( dst_start > src_start ) )
1899 	done -= N ;
1900 	else
1901 	done += N ;
1902 	}
1903 	
1904 	if ( succes )
1905 	operationdetail .get_last_child() .add_child( OperationDetail( String::ucompose( _("optimal blocksize is %1 sectors (%2)"),
1906 	optimal_blocksize,
1907 	Utils::format_size( optimal_blocksize ) ),
1908 	STATUS_NONE ) ) ;
1909 	
1910 	if ( succes )
1911 	succes = copy_blocks( src_device,
1912 	dst_device,
1913 	src_start + ( dst_start > src_start ? 0 : done ),
1914 	dst_start + ( dst_start > src_start ? 0 : done ),
1915 	length - llabs( done ),
1916 	optimal_blocksize,
1917 	operationdetail,
1918 	readonly,
1919 	total_done ) ;
1920 	
1921 	operationdetail .add_child( OperationDetail(
1922 	String::ucompose( readonly ? _("%1 sectors read") : _("%1 sectors copied"), total_done ), STATUS_NONE ) ) ;
1923 	return succes ;
1924 	} 
```

As you can notice, in order to calculate the adequate block size, it starts out with an initial block size: benchmark_blocksize,
hence if its elapsed time during copying is smaller, then it's assigned to optimal_blocksize. then double benchmar_blocksize and iterate through another loop process.

I was wondering is this algorithm efficient enough ?

Thanks a lot,

---


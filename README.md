# OP25
Branch of OP25 enabling UDP packet output of 25 Data for Wireshark. 

more info here: http://op25.osmocom.org/trac/wiki

	sudo apt-get build-dep gnuradio
	sudo apt-get install gnuradio gnuradio-dev gr-osmosdr librtlsdr-dev libuhd-dev  libhackrf-dev libitpp-dev libpcap-dev git
	sudo apt-get install bison flex libgtk2.0-dev libpcap-dev subversion

OP25:

	cd ~
	git clone git://op25.osmocom.org/op25.git
	cd op25
	mkdir build
	cd build
	cmake ../
	make
	sudo make install
	sudo ldconfig

UPDATED wireshark installation: 

Note: ONLY version 1.6.5 seems to be happy compiling these days with the P25 plugin!!

	mkdir -p SourceCode
	cd SourceCode
	wget https://www.wireshark.org/download/src/all-versions/wireshark-1.6.5.tar.bz2
	tar xjvf wireshark-1.6.5.tar.bz2
	cd wireshark-1.6.5
	(cd plugins && svn checkout http://op25.osmocom.org/svn/trunk/wireshark/plugins/p25 p25)
	svn checkout http://op25.osmocom.org/svn/trunk/wireshark/patches
	patch -p1 < patches/wireshark-1.6.5.patch
	./autogen.sh && ./configure && make clean && make
	sudo make install
	sudo ldconfig

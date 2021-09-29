all: hello.efi

%.o: %.c
	clang -target x86_64-pc-win32-coff -o $@ -c $<

%.efi: %.o
	lld-link /subsystem:efi_application /entry:EfiMain /out:$@ $<

.PHONY: run
run: hello.efi
	./run_qemu.sh hello.efi

clean:
	rm -f disk.img
	rm -f hello.efi
	rm -rf mnt

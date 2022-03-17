# PatternScanner

Simple pattern scanner based on the 2 sources in the credits

Example Usage.
```cpp
  Example pattern with '?' being the wildcard - 2B ? 2B ? 55 ? 45 ?
  
  HMODULE GameModule = GetModuleHandle(NULL);
  const uint64 BaseAddress = reinterpret_cast<uint64>(GameModule);
  const IMAGE_DOS_HEADER* DOSHeader = reinterpret_cast<IMAGE_DOS_HEADER*>(GameModule);
  const IMAGE_NT_HEADERS* NtHeaders = reinterpret_cast<IMAGE_NT_HEADERS*>(reinterpret_cast<long long>(GameModule) + DOSHeader->e_lfanew);
  const DWORD SizeOfImage = NtHeaders->OptionalHeader.SizeOfImage;

  T* Result = PatternScan<T*>("4D 5A ? 00", BaseAddress, SizeOfImage);   
  INT VTableIndex = ScanVTable("48 89 ? 24 ? 57", Object);
```


Credits:

lguilhermee - https://github.com/lguilhermee/Discord-DX11-Overlay-Hook/blob/master/Helper/Helper.cpp

guttir14 - https://github.com/guttir14/CheatIt/blob/main/CheatIt/utils.cpp

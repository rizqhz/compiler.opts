<h3 align="center">
    <pre>compiler.opts</pre>
</h3>

<div align="center">
    <em>"A Collection of Compiler and Linker Configurations for Performance Tuning and Binary Optimization"</em>
</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

### Overview

<div align="justify">

**compiler.opts** is a collection of compiler and linker configurations designed to provide performance-oriented build profiles for software compilation. The project brings together various configurations for **GCC** and **Clang/LLVM**, incorporating different compiler flags, linker options, and optimization techniques to explore different approaches to improving build performance and binary output. Each configuration offers a distinct combination of compiler and linker settings, allowing users to choose and experiment with different optimization strategies based on their toolchain, target architecture, and specific requirements.

The project aims to provide a flexible and maintainable collection of build configurations that can evolve alongside compiler technologies and optimization techniques. Rather than enforcing a universal configuration, **compiler.opts** encourages experimentation, benchmarking, and informed configuration choices to achieve a suitable balance between performance, compatibility, build efficiency, and binary characteristics.

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

### Features

<div align="justify">

- **Multiple Compiler Support**  
  Provides dedicated configuration profiles for `GCC` and `Clang/LLVM` toolchains.

- **Flexible Linker Selection**  
  Supports multiple linkers, including GNU `bfd`, LLVM `lld`, `mold`, and `wild`, depending on the selected configuration.

- **Optimization-Oriented Configurations**  
  Includes various compiler and linker flags designed to improve compilation output, runtime performance, and binary characteristics.

- **Link-Time Optimization (LTO)**  
  Provides LTO-enabled profiles for GCC and Clang to enable cross-module optimization during the linking stage.

- **Architecture-Specific Optimization**  
  Includes target-specific compiler settings to take advantage of processor features and instruction sets.

- **Multi-Language Build Support**  
  Provides compiler configurations for `C`, `C++`, `Fortran`, and `Rust`.

- **Modular Configuration Profiles**  
  Offers separate configuration files with different compiler, linker, and optimization combinations, allowing users to select profiles according to their requirements.

- **Extensible Configuration Design**  
  Maintains a flexible structure that can accommodate additional optimization techniques, toolchains, and configuration profiles as the project evolves.

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

### Available Configurations

<div align="justify">

**compiler.opts** currently provides 13 configuration profiles, organized into three categories: a default profile, GCC-based profiles, and Clang/LLVM-based profiles. Each profile offers a different combination of compiler, linker, and optimization settings, allowing users to choose configurations that best suit their build environment and requirements.

</div>

<div align="center">

#### Configuration Overview

The following table provides a quick comparison of all available profiles.

| Configuration         | Compiler              | Linker | LTO | PGO |
|-----------------------|-----------------------|:------:|:---:|:---:|
| `default.conf`        | *Environment default* | `bfd`  | No  | -   |
| `gcc.conf`            | `gcc`                 | `bfd`  | No  | -   |
| `gcc-lto.conf`        | `gcc`                 | `bfd`  | Yes | -   |
| `gcc-mold.conf`       | `gcc`                 | `mold` | No  | -   |
| `gcc-mold-lto.conf`   | `gcc`                 | `mold` | Yes | -   |
| `gcc-wild.conf`       | `gcc`                 | `wild` | No  | -   |
| `gcc-wild-lto.conf`   | `gcc`                 | `wild` | Yes | -   |
| `clang.conf`          | `clang`               | `lld`  | No  | -   |
| `clang-lto.conf`      | `clang`               | `lld`  | Yes | -   |
| `clang-mold.conf`     | `clang`               | `mold` | No  | -   |
| `clang-mold-lto.conf` | `clang`               | `mold` | Yes | -   |
| `clang-wild.conf`     | `clang`               | `wild` | No  | -   |
| `clang-wild-lto.conf` | `clang`               | `wild` | Yes | -   |

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

#### Default Configuration

<div align="justify">

`default.conf` provides a general-purpose configuration profile using GNU BFD as its linker.

Unlike the GCC and Clang profiles, this configuration does not explicitly specify compiler executables, allowing the build environment to determine which compiler toolchain to use. It provides common optimization flags and settings for C, C++, Fortran, and Rust builds.

</div>

#### GCC Profiles

<div align="justify">

GCC profiles use the GNU Compiler Collection as their primary compiler toolchain, with support for GCC's optimization capabilities, including Graphite-based loop transformations and vectorization.

</div>

<div align="center">

| Configuration       | Description                                                                |
|---------------------|----------------------------------------------------------------------------|
| `gcc.conf`          | Standard GCC profile using GNU BFD without LTO.                            |
| `gcc-lto.conf`      | GCC profile with Link-Time Optimization and linker plugin support.         |
| `gcc-mold.conf`     | GCC profile using mold as its linker, without LTO.                         |
| `gcc-mold-lto.conf` | Combines GCC, mold, and Link-Time Optimization.                            |
| `gcc-wild.conf`     | GCC profile using Wild as its linker, without LTO.                         |
| `gcc-wild-lto.conf` | Combines GCC, Wild, and Link-Time Optimization with linker plugin support. |

</div>

<div align="justify">

The GCC profiles share a common set of optimization techniques, with variations in linker selection and LTO configuration.

</div>

#### Clang Profiles

<div align="justify">

Clang profiles use the LLVM compiler infrastructure, including LLVM-based tools and Polly optimization capabilities. They provide multiple linker alternatives and support LLVM's Full Link-Time Optimization.

</div>

<div align="center">

| Configuration         | Description                                               |
|-----------------------|-----------------------------------------------------------|
| `clang.conf`          | Standard Clang profile using LLD without LTO.             |
| `clang-lto.conf`      | Clang profile using LLD with Full Link-Time Optimization. |
| `clang-mold.conf`     | Clang profile using mold as its linker, without LTO.      |
| `clang-mold-lto.conf` | Combines Clang, mold, and Full Link-Time Optimization.    |
| `clang-wild.conf`     | Clang profile using Wild as its linker, without LTO.      |
| `clang-wild-lto.conf` | Combines Clang, Wild, and Full Link-Time Optimization.    |

</div>

<div align="justify">

The Clang profiles also incorporate LLVM Polly for loop optimization and parallelization. LTO-enabled variants additionally introduce whole-program optimization options where supported by the selected toolchain.

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

#### Configuration Differences

<div align="justify">

Although the profiles share several optimization settings, their primary differences are determined by the compiler toolchain, linker implementation, and LTO configuration.

- **Compiler:** GCC and Clang use different optimization infrastructures and compiler-specific options.
- **Linker:** GNU BFD, LLD, mold, and Wild provide different linking implementations and capabilities.
- **LTO:** LTO-enabled profiles allow optimization across compilation units during the linking stage.
- **Linker Optimizations:** Certain profiles enable Identical Code Folding (ICF), while others use different linker-specific settings.

</div>

#### Important Notes

<div align="justify">

- All currently available profiles target the x86-64 Skylake microarchitecture through `-march=skylake`. Ensure that the target system supports the required instruction set features before using the resulting binaries.
- LTO-enabled configurations may require additional linker, plugin, and compiler compatibility.
- Wild-based LTO configurations should be tested against the specific Wild and compiler versions being used.
- Configuration profiles include aggressive optimization flags that may affect numerical behavior, compatibility, and security hardening.

*Review the relevant configuration and its requirements before applying it to a build environment.*

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

### Optimization Techniques

<div align="justify">

The configuration profiles incorporate various compiler and linker optimization techniques to improve code generation, execution performance, and binary characteristics. These techniques are applied differently across GCC and Clang/LLVM profiles, depending on their respective compiler capabilities and linker implementations.

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

#### Compiler Optimization

<div align="justify">

The profiles use a combination of standard optimization levels and additional compiler-specific options.

Most C and C++ profiles use `-O2` as their baseline optimization level, complemented by manually specified optimization flags. These options allow the compiler to apply additional transformations beyond the default optimization settings.

Architecture-specific compilation is also enabled through `-march=skylake`, allowing generated code to take advantage of supported instruction sets and processor features.

</div>

#### Loop Optimization and Parallelization

<div align="justify">

Loop optimization techniques are used to improve execution efficiency by transforming loop structures, reducing unnecessary operations, and improving data locality.

The project uses different approaches depending on the compiler:

</div>

#### Graphite

<div align="justify">

GCC profiles incorporate Graphite-based optimizations through options such as:

- `-fgraphite`
- `-fgraphite-identity`
- `-floop-interchange`
- `-floop-nest-optimize`
- `-floop-parallelize-all`
- `-floop-unroll-and-jam`

These transformations target loop nesting, data locality, parallelization opportunities, and loop execution efficiency.

</div>

#### Polly

<div align="justify">

Clang profiles use LLVM Polly for loop analysis and optimization through options such as:

- `-mllvm -polly`
- `-mllvm -polly-parallel`
- `-mllvm -polly-num-threads=8`
- `-mllvm -polly-vectorizer=stripmine`
- `-mllvm -polly-scheduling=dynamic`
- `-mllvm -polly-omp-backend=LLVM`

Polly provides a polyhedral optimization framework that can transform suitable loop structures and generate parallel code.

</div>

#### Automatic Vectorization

<div align="justify">

Vectorization allows compilers to process multiple data elements using SIMD instructions, potentially improving the performance of operations that can be executed in parallel.

The profiles enable vectorization through compiler-specific options, including:

- `-ftree-vectorize`
- `-fvectorize`
- `-fvect-cost-model=very-cheap`

These options help the compiler identify and transform suitable operations into vectorized instructions.

The effectiveness of vectorization depends on the code structure, data dependencies, target architecture, and compiler capabilities.

</div>

#### Floating-Point Optimization

<div align="justify">

The profiles include relaxed floating-point optimization options to provide the compiler with additional freedom when transforming mathematical operations.

Some of the options used include:

- `-fno-math-errno`
- `-fno-signed-zeros`
- `-fno-rounding-math`
- `-fno-trapping-math`
- `-fassociative-math`
- `-freciprocal-math`
- `-ffinite-math-only`
- `-ffp-contract=fast`
- `-fexcess-precision=fast`

These options allow transformations such as mathematical expression reassociation, reciprocal-based calculations, and floating-point operation contraction. However, relaxed floating-point semantics may change numerical results, rounding behavior, and the handling of exceptional floating-point values.

Applications that require strict numerical accuracy or IEEE 754 compliance should be carefully tested before using these options.

</div>

#### Link-Time Optimization (LTO)

<div align="justify">

Link-Time Optimization enables the compiler to perform additional optimization across compilation units during the linking stage. The project provides LTO-enabled profiles for both GCC and Clang.

</div>

#### GCC LTO

<div align="justify">

GCC profiles use:

- `-flto`
- `-fuse-linker-plugin`

These options enable interprocedural optimization across translation units and allow the linker plugin to participate in the LTO process.

</div>

#### Clang Full LTO

<div align="justify">

Clang profiles use:

- `-flto=full`
- `-Wl,--lto-O3` (where configured)
- `-Wl,--lto-whole-program-visibility` (where configured)

Additional C++ optimizations are enabled in LTO profiles through options such as:

- `-fwhole-program-vtables`
- `-fvirtual-function-elimination`

These techniques provide opportunities for additional whole-program optimization, particularly when analyzing C++ virtual function usage.

*LTO may increase compilation and linking time as well as memory consumption. Its actual performance benefits depend on the application and workload.*

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

#### Linker Optimization

<div align="justify">

Linker-level optimization techniques are used to improve the linking process and refine the resulting binary.

The profiles incorporate several linker options, including:

</div>

<div align="center">

| Option          | Purpose                                                              |
|-----------------|----------------------------------------------------------------------|
| `--gc-sections` | Removes unused sections from the output binary.                      |
| `--icf=all`     | Enables Identical Code Folding to merge eligible identical sections. |
| `--icf=none`    | Disables Identical Code Folding.                                     |
| `--as-needed`   | Avoids unnecessary shared library dependencies where applicable.     |
| `--relax`       | Enables supported target-specific linker relaxations.                |
| `--sort-common` | Controls the ordering of common symbols.                             |
| `--threads=8`   | Configures up to eight linker threads where supported.               |
| `-O2` / `-O3`   | Selects the linker's optimization level where supported.             |

</div>

<div align="justify">

The profiles also combine `-fdata-sections` and `-ffunction-sections` with `--gc-sections` to allow unused data and functions to be removed at link time.

Identical Code Folding is enabled in selected BFD alternatives where supported, LLD, and mold profiles, while Wild profiles explicitly disable it.

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

#### Rust Optimization

<div align="justify">

Rust build settings are also included through `RUSTFLAGS`, providing optimization options for Rust-based components.

The profiles commonly use:

- `-C opt-level=3` — Enables a high optimization level for generated code.
- `-C target-cpu=skylake` — Targets the Skylake microarchitecture.
- `-C codegen-units=1` — Uses a single code generation unit per crate.
- `-C strip=symbols` — Removes symbols from the generated output.
- `-C overflow-checks=off` — Disables runtime integer overflow checks.
- `-C panic=abort` — Uses process abortion instead of stack unwinding when a panic occurs.

Clang LTO profiles additionally enable Rust linker-plugin LTO through `-C linker-plugin-lto`.

These settings prioritize optimized code generation and reduced binary overhead, although some of them introduce behavioral and compatibility trade-offs.

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

#### Binary Size and Output Optimization

<div align="justify">

Several options are included to reduce unnecessary binary content and refine the final output.

These include:

- Section garbage collection through `--gc-sections`.
- Identical Code Folding through `--icf=all` where enabled.
- Debug information removal through `--strip-debug`.
- Symbol table removal through `--strip-all`.
- Relative relocation packing through `-z pack-relative-relocs`.

These techniques can reduce binary size and eliminate unnecessary sections or metadata.

However, removing debugging information and symbols can make debugging, profiling, and post-build inspection more difficult.

</div>

<h6 align="center">
    <samp>• • •</samp>
</h6>

#### Optimization Considerations

<div align="justify">

The optimization techniques provided by this project involve different trade-offs and should not be considered universally beneficial.

- **Architecture Dependency:** Profiles targeting Skylake require compatible CPU features on the target system.
- **Workload Dependency:** Loop transformations, vectorization, and other compiler optimizations may produce different results depending on application characteristics.
- **Floating-Point Accuracy:** Relaxed mathematical assumptions can change numerical behavior.
- **Build Resources:** LTO and certain advanced optimization passes may increase compilation time and memory consumption.
- **Linker Compatibility:** Some linker options are specific to particular linker implementations and versions.
- **Runtime Behavior:** Certain optimization flags change runtime checks, panic handling, and other program behavior.

</div>

<h6 align="center"></h6>

<hr>

<div align=center>
    <samp><a href="#readme">BACK TO TOP</a></samp>
</div>

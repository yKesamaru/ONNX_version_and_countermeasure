# ONNXのライブラリ依存とその解決法

![](assets/eye-catch.png)

## はじめに

## `ONNX`とNvidiaライブラリの関係

## 具体的なエラーメッセージ
```bash
2024-07-15 09:55:28.305600246 [E:onnxruntime:Default, provider_bridge_ort.cc:1745 TryGetProviderInfo_CUDA] /onnxruntime_src/onnxruntime/core/session/provider_bridge_ort.cc:1426 onnxruntime::Provider& onnxruntime::ProviderLibrary::Get() [ONNXRuntimeError] : 1 : FAIL : Failed to load library libonnxruntime_providers_cuda.so with error: libcudnn.so.9: cannot open shared object file: No such file or directory

2024-07-15 09:55:28.305630883 [W:onnxruntime:Default, onnxruntime_pybind_state.cc:895 CreateExecutionProviderInstance] Failed to create CUDAExecutionProvider. Please reference https://onnxruntime.ai/docs/execution-providers/CUDA-ExecutionProvider.html#requirementsto ensure all dependencies are met.
```
日本語訳
```
2024-07-15 09:55:28.305600246 [E:onnxruntime:Default, provider_bridge_ort.cc:1745 TryGetProviderInfo_CUDA] /onnxruntime_src/onnxruntime/core/session/provider_bridge_ort.cc:1426 onnxruntime::Provider& onnxruntime::ProviderLibrary::Get() [ONNXRuntimeError] : 1 : FAIL : ライブラリ libonnxruntime_providers_cuda.so の読み込みに失敗しました。エラー内容: libcudnn.so.9: 共有オブジェクトファイルを開けません: そのようなファイルやディレクトリはありません

2024-07-15 09:55:28.305630883 [W:onnxruntime:Default, onnxruntime_pybind_state.cc:895 CreateExecutionProviderInstance] CUDAExecutionProvider の作成に失敗しました。すべての依存関係が満たされていることを確認するには、https://onnxruntime.ai/docs/execution-providers/CUDA-ExecutionProvider.html#requirements を参照してください。
```

（意訳）
ONNX RuntimeがCUDAの実行プロバイダをロードしようとしたときに発生しているエラー。

1. **libonnxruntime_providers_cuda.so**というライブラリの読み込みに失敗しました。
2. 依存関係である**`libcudnn.so.9`**(CUDAの一部であるcuDNNライブラリ)というファイルが見つからないことが原因。
3. 結果として、`CUDA Execution Provider`の作成に失敗しました。


### 補足
#### `CUDA Execution Provider`
`ONNX Runtime`の実行プロバイダの一つ。
`pip install onnxruntime-gpu`にて導入する。
- [ONNX Runtime - Execution Providers Documentation](https://onnxruntime.ai/docs/execution-providers/)
- [NVIDIA Developer - CUDA Toolkit Documentation](https://developer.nvidia.com/cuda-toolkit)
- [ONNX Runtime GitHub Repository](https://github.com/microsoft/onnxruntime)
- [ONNX Runtime - CUDA Execution Provider Requirements](https://onnxruntime.ai/docs/execution-providers/CUDA-ExecutionProvider.html#requirements)




## 対処法
### Dock`er

### `GNOME Boxes`

### リンクの作成


## 最後に

## 参考文献
- [ONNX Runtimeの公式ドキュメント](https://onnxruntime.ai/docs/execution-providers/CUDA-ExecutionProvider.html#requirements)
- [ONNX Runtime - Execution Providers Documentation](https://onnxruntime.ai/docs/execution-providers/)
- [NVIDIA Developer - CUDA Toolkit Documentation](https://developer.nvidia.com/cuda-toolkit)
- [ONNX Runtime GitHub Repository](https://github.com/microsoft/onnxruntime)
- [ONNX Runtime - CUDA Execution Provider Requirements](https://onnxruntime.ai/docs/execution-providers/CUDA-ExecutionProvider.html#requirements)


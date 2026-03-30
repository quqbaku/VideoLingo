# VideoLingo 开发文档

## 部署状态

### 已完成
- [x] Python 3.10 虚拟环境（使用 uv）
- [x] PyTorch 2.8.0 + CUDA 12.6
- [x] FFmpeg（复制自 Jellyfin，支持 NVIDIA NVENC）
- [x] 核心依赖：whisperx, demucs, transformers, streamlit 等
- [x] NVIDIA GeForce RTX 3070 Ti GPU 已识别
- [x] Streamlit 应用运行于 http://localhost:8501

### 环境路径
```
项目根目录: c:\Users\85273\Desktop\VideoLingo\VideoLingo
虚拟环境:   .venv
临时FFmpeg: _temp_bin\ffmpeg.exe
启动命令:   .venv\Scripts\streamlit.exe run st.py
```

### 待配置
- [ ] MiniMax API 密钥（Web 界面配置）
- [ ] FFmpeg 建议添加到系统 PATH（当前在 _temp_bin）

---

## 离线/在线方案对比

### 大模型（翻译/总结）

| 方案 | 模型 | 费用 | 效果 | 配置难度 |
|------|------|------|------|----------|
| 在线 API | MiniMax 2.7 | 低 | 😃 | 已配置 |
| 在线 API | Claude 3.5 Sonnet | 中 | 🤩 | 需申请 |
| 在线 API | GPT-4o | 中 | 🤩 | 需申请 |
| **离线** | Ollama + qwen3-32b | 免费 | 😃 | 需安装 |

### TTS 配音

| 方案 | 费用 | 中文效果 | 配置难度 |
|------|------|----------|----------|
| **离线 Edge TTS** | 免费 | 😐 一般 | ✅ 已就绪 |
| 302.ai Azure TTS | 低 | 🤩 好 | 需注册 |
| SiliconFlow FishTTS | 低 | 😃 | 需注册 |
| **离线 GPT-SoVITS** | 免费 | 🏆 最佳 | 复杂需训练 |

---

## 下次开发待办

### 高优先级
1. 配置 MiniMax API 密钥（或切换到更强模型）
2. 测试完整视频翻译流程
3. 评估配音效果

### 可选优化
1. 安装 Ollama 实现完全离线翻译
2. 配置 GPT-SoVITS 实现高质量语音克隆
3. 将 FFmpeg 添加到系统 PATH

---

## 快速启动

```bash
# 进入项目目录
cd c:\Users\85273\Desktop\VideoLingo\VideoLingo

# 启动 Streamlit（需先设置 PATH）
set PATH=%CD%\_temp_bin;%PATH%
.venv\Scripts\streamlit.exe run st.py
```

---

## 技术栈

- **框架**: Python 3.10 + Streamlit
- **GPU**: PyTorch CUDA 12.6 (RTX 3070 Ti)
- **ASR**: WhisperX (large-v3 模型)
- **音频分离**: Demucs
- **视频处理**: FFmpeg + MoviePy
- **翻译**: 支持 OpenAI 格式 API (MiniMax/Claude/GPT/Ollama)
- **TTS**: Edge TTS / Azure TTS / Fish TTS / GPT-SoVITS

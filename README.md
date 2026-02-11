<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>财启星盘 · 家居财能空间诊断</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-dark: #0a0a14;
            --secondary-dark: #1a1a2e;
            --accent-gold: #d4af37;
            --accent-light: #f5e8b5;
            --text-primary: #f0f0f0;
            --text-secondary: #b0b0c0;
            --success: #2ecc71;
            --warning: #f39c12;
            --danger: #e74c3c;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background-color: var(--primary-dark);
            color: var(--text-primary);
            line-height: 1.6;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(42, 44, 78, 0.2) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(212, 175, 55, 0.1) 0%, transparent 20%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* 头部样式 */
        header {
            padding: 30px 0 20px;
            text-align: center;
            border-bottom: 1px solid rgba(212, 175, 55, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 15px;
        }
        
        .logo-icon {
            font-size: 2.5rem;
            color: var(--accent-gold);
            margin-right: 15px;
        }
        
        .logo-text h1 {
            font-size: 2.2rem;
            background: linear-gradient(to right, var(--accent-gold), var(--accent-light));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 2px;
        }
        
        .logo-text .subtitle {
            color: var(--text-secondary);
            font-size: 0.9rem;
            letter-spacing: 3px;
            margin-top: 5px;
        }
        
        .tagline {
            font-size: 1.1rem;
            color: var(--accent-light);
            max-width: 700px;
            margin: 0 auto;
            line-height: 1.8;
        }
        
        /* 进度指示器 */
        .progress-container {
            display: flex;
            justify-content: center;
            margin: 30px auto;
            max-width: 800px;
        }
        
        .progress-step {
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
            width: 25%;
        }
        
        .step-number {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: var(--secondary-dark);
            color: var(--text-secondary);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            margin-bottom: 10px;
            border: 2px solid var(--secondary-dark);
            transition: all 0.3s ease;
            z-index: 2;
        }
        
        .step-number.active {
            background-color: var(--accent-gold);
            color: var(--primary-dark);
            border-color: var(--accent-light);
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.5);
        }
        
        .step-number.completed {
            background-color: var(--success);
            color: white;
            border-color: var(--success);
        }
        
        .step-text {
            font-size: 0.85rem;
            color: var(--text-secondary);
            text-align: center;
        }
        
        .progress-step:not(:last-child)::after {
            content: '';
            position: absolute;
            top: 20px;
            left: 70px;
            width: calc(100% - 40px);
            height: 2px;
            background-color: var(--secondary-dark);
            z-index: 1;
        }
        
        .progress-step.active::after {
            background-color: var(--secondary-dark);
        }
        
        .progress-step.completed::after {
            background-color: var(--success);
        }
        
        /* 测试区域 */
        .test-container {
            background-color: var(--secondary-dark);
            border-radius: 15px;
            padding: 40px;
            margin: 30px 0;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(212, 175, 55, 0.1);
            position: relative;
        }
        
        .test-container::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, var(--accent-gold), transparent, var(--accent-gold));
            border-radius: 17px;
            z-index: -1;
            opacity: 0.1;
        }
        
        .step-content {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .step-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .step-title {
            font-size: 1.8rem;
            color: var(--accent-light);
            margin-bottom: 25px;
            text-align: center;
            position: relative;
            padding-bottom: 15px;
        }
        
        .step-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 3px;
            background: linear-gradient(to right, transparent, var(--accent-gold), transparent);
        }
        
        /* 步骤1：用户信息 */
        .user-info-form {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-label {
            display: block;
            margin-bottom: 8px;
            color: var(--accent-light);
            font-size: 1.1rem;
        }
        
        .form-input, .form-select {
            width: 100%;
            padding: 14px 18px;
            background-color: rgba(10, 10, 20, 0.7);
            border: 1px solid rgba(212, 175, 55, 0.3);
            border-radius: 8px;
            color: var(--text-primary);
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        
        .form-input:focus, .form-select:focus {
            outline: none;
            border-color: var(--accent-gold);
            box-shadow: 0 0 0 2px rgba(212, 175, 55, 0.2);
        }
        
        /* 步骤2：房屋布局 */
        .layout-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .layout-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            grid-template-rows: repeat(3, 1fr);
            gap: 10px;
            width: 300px;
            height: 300px;
            margin: 30px auto;
            position: relative;
        }
        
        .grid-cell {
            background-color: rgba(10, 10, 20, 0.7);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 5px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            padding: 10px;
        }
        
        .grid-cell:hover {
            border-color: var(--accent-gold);
            transform: translateY(-5px);
        }
        
        .grid-cell.selected {
            border-color: var(--accent-gold);
            background-color: rgba(212, 175, 55, 0.1);
            box-shadow: 0 5px 15px rgba(212, 175, 55, 0.2);
        }
        
        .direction-label {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--accent-gold);
        }
        
        .position-label {
            font-size: 0.8rem;
            color: var(--text-secondary);
            margin-top: 5px;
        }
        
        .item-icon {
            margin-top: 8px;
            font-size: 1.5rem;
            color: var(--accent-light);
        }
        
        .item-selector {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            margin-top: 30px;
        }
        
        .item-option {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 15px;
            background-color: rgba(10, 10, 20, 0.7);
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            cursor: pointer;
            transition: all 0.3s ease;
            width: 120px;
        }
        
        .item-option:hover {
            border-color: var(--accent-gold);
            transform: translateY(-5px);
        }
        
        .item-option.selected {
            border-color: var(--accent-gold);
            background-color: rgba(212, 175, 55, 0.1);
        }
        
        .item-option i {
            font-size: 2rem;
            margin-bottom: 10px;
            color: var(--accent-gold);
        }
        
        /* 步骤3：能量评估 */
        .energy-assessment {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .energy-question {
            background-color: rgba(10, 10, 20, 0.5);
            border-radius: 10px;
            padding: 25px;
            margin-bottom: 25px;
            border-left: 4px solid var(--accent-gold);
        }
        
        .question-text {
            font-size: 1.2rem;
            margin-bottom: 20px;
            color: var(--accent-light);
        }
        
        .options-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 15px;
        }
        
        .option {
            padding: 15px;
            background-color: rgba(255, 255, 255, 0.05);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 1px solid transparent;
        }
        
        .option:hover {
            background-color: rgba(212, 175, 55, 0.1);
            border-color: rgba(212, 175, 55, 0.3);
        }
        
        .option.selected {
            background-color: rgba(212, 175, 55, 0.15);
            border-color: var(--accent-gold);
        }
        
        /* 步骤4：结果报告 */
        .result-container {
            max-width: 900px;
            margin: 0 auto;
        }
        
        .report-header {
            text-align: center;
            margin-bottom: 40px;
        }
        
        .report-title {
            font-size: 2.2rem;
            background: linear-gradient(to right, var(--accent-gold), var(--accent-light));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 15px;
        }
        
        .user-summary {
            color: var(--text-secondary);
            font-size: 1.1rem;
        }
        
        .report-section {
            background-color: rgba(10, 10, 20, 0.5);
            border-radius: 10px;
            padding: 30px;
            margin-bottom: 30px;
            border-top: 3px solid var(--accent-gold);
        }
        
        .section-title {
            font-size: 1.5rem;
            color: var(--accent-light);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
        }
        
        .section-title i {
            margin-right: 10px;
            color: var(--accent-gold);
        }
        
        .energy-radar {
            display: flex;
            justify-content: center;
            margin: 30px 0;
        }
        
        .radar-chart {
            position: relative;
            width: 300px;
            height: 300px;
        }
        
        .radar-grid {
            position: absolute;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .radar-grid:nth-child(2) {
            transform: scale(0.66);
        }
        
        .radar-grid:nth-child(3) {
            transform: scale(0.33);
        }
        
        .radar-point {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: var(--accent-gold);
            border-radius: 50%;
            transform: translate(-50%, -50%);
        }
        
        .radar-label {
            position: absolute;
            color: var(--text-secondary);
            font-size: 0.9rem;
        }
        
        .solutions-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }
        
        .solution-card {
            background: linear-gradient(145deg, rgba(26, 26, 46, 0.8), rgba(10, 10, 20, 0.8));
            border-radius: 10px;
            padding: 25px;
            border-left: 4px solid var(--accent-gold);
        }
        
        .solution-title {
            font-size: 1.3rem;
            color: var(--accent-light);
            margin-bottom: 15px;
            display: flex;
            align-items: center;
        }
        
        .solution-title i {
            margin-right: 10px;
            color: var(--accent-gold);
        }
        
        .recommended-products {
            display: flex;
            overflow-x: auto;
            gap: 20px;
            padding: 20px 0;
        }
        
        .product-card {
            flex: 0 0 auto;
            width: 200px;
            background-color: rgba(10, 10, 20, 0.7);
            border-radius: 10px;
            overflow: hidden;
            border: 1px solid rgba(212, 175, 55, 0.2);
            transition: all 0.3s ease;
        }
        
        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
            border-color: var(--accent-gold);
        }
        
        .product-img {
            height: 150px;
            background-color: rgba(212, 175, 55, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: var(--accent-gold);
        }
        
        .product-info {
            padding: 15px;
        }
        
        .product-name {
            font-size: 1.1rem;
            color: var(--accent-light);
            margin-bottom: 8px;
        }
        
        .product-price {
            color: var(--accent-gold);
            font-weight: bold;
            font-size: 1.2rem;
            margin-bottom: 15px;
        }
        
        .btn-buy {
            display: block;
            width: 100%;
            padding: 10px;
            background-color: var(--accent-gold);
            color: var(--primary-dark);
            border: none;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
            text-decoration: none;
        }
        
        .btn-buy:hover {
            background-color: var(--accent-light);
            transform: translateY(-2px);
        }
        
        /* 按钮样式 */
        .btn {
            padding: 14px 30px;
            background-color: var(--accent-gold);
            color: var(--primary-dark);
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
        }
        
        .btn:hover {
            background-color: var(--accent-light);
            transform: translateY(-3px);
            box-shadow: 0 7px 15px rgba(212, 175, 55, 0.3);
        }
        
        .btn:disabled {
            background-color: var(--text-secondary);
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        
        .btn i {
            margin-right: 8px;
        }
        
        .btn-secondary {
            background-color: transparent;
            color: var(--accent-gold);
            border: 1px solid var(--accent-gold);
        }
        
        .btn-secondary:hover {
            background-color: rgba(212, 175, 55, 0.1);
        }
        
        .navigation-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 40px;
        }
        
        /* 分享按钮 */
        .share-container {
            text-align: center;
            margin-top: 40px;
            padding-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .share-title {
            color: var(--text-secondary);
            margin-bottom: 20px;
        }
        
        .share-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
        }
        
        .share-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .share-wechat {
            background-color: #09bb07;
        }
        
        .share-redbook {
            background-color: #ff2442;
        }
        
        .share-copy {
            background-color: var(--accent-gold);
        }
        
        .share-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        /* 底部 */
        footer {
            text-align: center;
            padding: 40px 0;
            color: var(--text-secondary);
            font-size: 0.9rem;
            border-top: 1px solid rgba(212, 175, 55, 0.1);
            margin-top: 50px;
        }
        
        .disclaimer {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: rgba(10, 10, 20, 0.5);
            border-radius: 10px;
            font-size: 0.85rem;
            line-height: 1.7;
        }
        
        /* 响应式设计 */
        @media (max-width: 768px) {
            .container {
                padding: 0 15px;
            }
            
            .logo-text h1 {
                font-size: 1.8rem;
            }
            
            .test-container {
                padding: 25px 20px;
            }
            
            .progress-step::after {
                display: none;
            }
            
            .progress-step {
                width: auto;
                margin: 0 10px;
            }
            
            .progress-container {
                flex-wrap: wrap;
            }
            
            .layout-grid {
                width: 250px;
                height: 250px;
            }
            
            .solutions-grid {
                grid-template-columns: 1fr;
            }
            
            .navigation-buttons {
                flex-direction: column;
                gap: 15px;
            }
            
            .btn {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- 头部 -->
        <header>
            <div class="logo">
                <div class="logo-icon">
                    <i class="fas fa-star-and-crescent"></i>
                </div>
                <div class="logo-text">
                    <h1>财启星盘</h1>
                    <div class="subtitle">HOME ENERGY DIAGNOSIS</div>
                </div>
            </div>
            <p class="tagline">基于千年风水智慧与现代环境心理学，诊断您的家居财能格局，提供个性化能量优化方案</p>
        </header>

        <!-- 进度指示器 -->
        <div class="progress-container">
            <div class="progress-step completed" id="step1-indicator">
                <div class="step-number">1</div>
                <div class="step-text">个人信息</div>
            </div>
            <div class="progress-step active" id="step2-indicator">
                <div class="step-number">2</div>
                <div class="step-text">房屋布局</div>
            </div>
            <div class="progress-step" id="step3-indicator">
                <div class="step-number">3</div>
                <div class="step-text">能量评估</div>
            </div>
            <div class="progress-step" id="step4-indicator">
                <div class="step-number">4</div>
                <div class="step-text">诊断报告</div>
            </div>
        </div>

        <!-- 测试容器 -->
        <div class="test-container">
            <!-- 步骤1：用户信息 -->
            <div class="step-content active" id="step1">
                <h2 class="step-title">第一步：个人信息与能量基础</h2>
                <form class="user-info-form">
                    <div class="form-group">
                        <label class="form-label">您的称呼</label>
                        <input type="text" class="form-input" id="user-name" placeholder="请输入您的姓名或昵称">
                    </div>
                    <div class="form-group">
                        <label class="form-label">出生年份</label>
                        <select class="form-select" id="birth-year">
                            <option value="">请选择出生年份</option>
                            <!-- 年份选项由JavaScript生成 -->
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">您的职业类型</label>
                        <select class="form-select" id="career-type">
                            <option value="">请选择最接近的职业类型</option>
                            <option value="metal">金融/法律/管理（金）</option>
                            <option value="wood">教育/文化/创意（木）</option>
                            <option value="water">贸易/物流/咨询（水）</option>
                            <option value="fire">科技/能源/餐饮（火）</option>
                            <option value="earth">房地产/建筑/农业（土）</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">近期最大财务困惑</label>
                        <select class="form-select" id="financial-issue">
                            <option value="">请选择最困扰您的财务问题</option>
                            <option value="income">收入增长停滞，努力无果</option>
                            <option value="opportunity">机会总是擦肩而过</option>
                            <option value="saving">存不住钱，莫名消耗</option>
                            <option value="investment">投资决策常出错</option>
                            <option value="balance">收支难以平衡</option>
                        </select>
                    </div>
                </form>
                <div class="navigation-buttons">
                    <button class="btn btn-secondary" disabled>
                        <i class="fas fa-arrow-left"></i> 上一步
                    </button>
                    <button class="btn" id="next-to-step2">
                        下一步 <i class="fas fa-arrow-right"></i>
                    </button>
                </div>
            </div>

            <!-- 步骤2：房屋布局 -->
            <div class="step-content" id="step2">
                <h2 class="step-title">第二步：家居空间布局诊断</h2>
                <p style="text-align: center; margin-bottom: 30px; color: var(--text-secondary);">
                    请点击您家客厅中以下物品实际摆放的位置（以客厅中心为参考点）
                </p>
                
                <div class="layout-container">
                    <div class="layout-grid" id="layout-grid">
                        <!-- 网格单元格由JavaScript生成 -->
                    </div>
                    
                    <div class="item-selector" id="item-selector">
                        <!-- 物品选项由JavaScript生成 -->
                    </div>
                </div>
                
                <div class="navigation-buttons">
                    <button class="btn btn-secondary" id="back-to-step1">
                        <i class="fas fa-arrow-left"></i> 上一步
                    </button>
                    <button class="btn" id="next-to-step3">
                        下一步 <i class="fas fa-arrow-right"></i>
                    </button>
                </div>
            </div>

            <!-- 步骤3：能量评估 -->
            <div class="step-content" id="step3">
                <h2 class="step-title">第三步：个人财能能量评估</h2>
                
                <div class="energy-assessment">
                    <div class="energy-question">
                        <div class="question-text">1. 当您进入家门时，通常的第一感觉是？</div>
                        <div class="options-container">
                            <div class="option" data-value="crowded">A. 有点拥挤，物品较多</div>
                            <div class="option" data-value="empty">B. 空旷冷清，缺乏生气</div>
                            <div class="option" data-value="bright">C. 明亮舒适，心情放松</div>
                            <div class="option" data-value="dark">D. 昏暗沉闷，想尽快离开</div>
                        </div>
                    </div>
                    
                    <div class="energy-question">
                        <div class="question-text">2. 您家中是否有堆积超过半年未处理的旧物或杂物？</div>
                        <div class="options-container">
                            <div class="option" data-value="many">A. 很多，各个角落都有</div>
                            <div class="option" data-value="some">B. 有一些，主要在储藏室</div>
                            <div class="option" data-value="few">C. 很少，定期清理</div>
                            <div class="option" data-value="none">D. 几乎没有，保持极简</div>
                        </div>
                    </div>
                    
                    <div class="energy-question">
                        <div class="question-text">3. 您家中的绿植或水元素（鱼缸、流水摆件等）状况如何？</div>
                        <div class="options-container">
                            <div class="option" data-value="lush">A. 茂盛生长，维护良好</div>
                            <div class="option" data-value="some-dead">B. 有一些但状态不佳</div>
                            <div class="option" data-value="none">C. 几乎没有这类元素</div>
                            <div class="option" data-value="artificial">D. 只有人造装饰</div>
                        </div>
                    </div>
                    
                    <div class="energy-question">
                        <div class="question-text">4. 您的财务状况让您感到最有压力的是？</div>
                        <div class="options-container">
                            <div class="option" data-value="stagnation">A. 收入停滞，缺乏增长</div>
                            <div class="option" data-value="instability">B. 波动太大，缺乏稳定</div>
                            <div class="option" data-value="leakage">C. 莫名其妙的花销</div>
                            <div class="option" data-value="opportunity">D. 抓不住好机会</div>
                        </div>
                    </div>
                </div>
                
                <div class="navigation-buttons">
                    <button class="btn btn-secondary" id="back-to-step2">
                        <i class="fas fa-arrow-left"></i> 上一步
                    </button>
                    <button class="btn" id="generate-report">
                        <i class="fas fa-chart-bar"></i> 生成诊断报告
                    </button>
                </div>
            </div>

            <!-- 步骤4：结果报告 -->
            <div class="step-content" id="step4">
                <div class="result-container">
                    <div class="report-header">
                        <h2 class="report-title">家居财能空间诊断报告</h2>
                        <div class="user-summary">
                            <span id="report-user-name">用户</span> · 
                            <span id="report-career-type">职业类型</span> · 
                            <span id="report-date">生成日期</span>
                        </div>
                    </div>
                    
                    <!-- 能量格局总览 -->
                    <div class="report-section">
                        <h3 class="section-title">
                            <i class="fas fa-compass"></i> 能量格局总览
                        </h3>
                        <p>基于您的个人信息与家居布局分析，您的财能格局在四个关键维度上的表现如下：</p>
                        
                        <div class="energy-radar">
                            <div class="radar-chart" id="radar-chart">
                                <!-- 雷达图由JavaScript生成 -->
                            </div>
                        </div>
                        
                        <div style="display: flex; justify-content: space-around; flex-wrap: wrap; margin-top: 30px;">
                            <div style="text-align: center; margin: 10px;">
                                <div style="font-size: 1.8rem; color: var(--accent-gold);" id="score-opportunity">0</div>
                                <div style="color: var(--text-secondary);">机遇敏感度</div>
                            </div>
                            <div style="text-align: center; margin: 10px;">
                                <div style="font-size: 1.8rem; color: var(--accent-gold);" id="score-risk">0</div>
                                <div style="color: var(--text-secondary);">风险抵御力</div>
                            </div>
                            <div style="text-align: center; margin: 10px;">
                                <div style="font-size: 1.8rem; color: var(--accent-gold);" id="score-stability">0</div>
                                <div style="color: var(--text-secondary);">积累稳定性</div>
                            </div>
                            <div style="text-align: center; margin: 10px;">
                                <div style="font-size: 1.8rem; color: var(--accent-gold);" id="score-help">0</div>
                                <div style="color: var(--text-secondary);">贵人运势</div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- 核心问题诊断 -->
                    <div class="report-section">
                        <h3 class="section-title">
                            <i class="fas fa-search"></i> 核心问题诊断
                        </h3>
                        <div id="problem-diagnosis">
                            <!-- 诊断内容由JavaScript生成 -->
                        </div>
                    </div>
                    
                    <!-- 定制化调整方案 -->
                    <div class="report-section">
                        <h3 class="section-title">
                            <i class="fas fa-tools"></i> 定制化调整方案
                        </h3>
                        <p>根据您的能量诊断结果，我们为您提供以下三步调整建议：</p>
                        
                        <div class="solutions-grid">
                            <div class="solution-card">
                                <h4 class="solution-title">
                                    <i class="fas fa-arrows-alt-h"></i> 移 · 清理阻塞
                                </h4>
                                <div id="solution-move">
                                    <!-- 移动方案由JavaScript生成 -->
                                </div>
                            </div>
                            
                            <div class="solution-card">
                                <h4 class="solution-title">
                                    <i class="fas fa-plus-circle"></i> 增 · 引入能量
                                </h4>
                                <div id="solution-add">
                                    <!-- 增加方案由JavaScript生成 -->
                                </div>
                            </div>
                            
                            <div class="solution-card">
                                <h4 class="solution-title">
                                    <i class="fas fa-gem"></i> 聚 · 核心强化
                                </h4>
                                <div id="solution-strengthen">
                                    <!-- 强化方案由JavaScript生成 -->
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- 推荐产品 -->
                    <div class="report-section">
                        <h3 class="section-title">
                            <i class="fas fa-crown"></i> 能量强化推荐
                        </h3>
                        <p>以下物品根据您的五行属性与能量需求特别推荐，可强化家居财能场：</p>
                        
                        <div class="recommended-products" id="recommended-products">
                            <!-- 推荐产品由JavaScript生成 -->
                        </div>
                    </div>
                    
                    <div class="share-container">
                        <h4 class="share-title">分享诊断报告，与好友一起提升财能</h4>
                        <div class="share-buttons">
                            <div class="share-btn share-wechat" title="分享到微信">
                                <i class="fab fa-weixin"></i>
                            </div>
                            <div class="share-btn share-redbook" title="分享到小红书">
                                <i class="fab fa-weibo"></i>
                            </div>
                            <div class="share-btn share-copy" title="复制报告链接" id="copy-link">
                                <i class="fas fa-link"></i>
                            </div>
                        </div>
                    </div>
                    
                    <div class="navigation-buttons">
                        <button class="btn btn-secondary" id="back-to-step3">
                            <i class="fas fa-redo"></i> 重新测试
                        </button>
                        <button class="btn" id="save-report">
                            <i class="fas fa-download"></i> 保存报告
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- 免责声明 -->
        <div class="disclaimer">
            <p><strong>免责声明：</strong>本测试基于传统风水学与环境心理学原理，旨在提供家居优化建议与积极心理暗示。所有结果仅供娱乐与参考，不构成投资或财务建议。财运提升需结合个人努力与理性决策，我们鼓励您以积极心态面对生活，通过实际行动创造美好未来。</p>
        </div>
        
        <footer>
            <p>© 2023 财启星盘 · 家居能量诊断系统 | 本内容仅供娱乐参考</p>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // 全局数据存储
            const userData = {
                name: '',
                birthYear: '',
                careerType: '',
                financialIssue: '',
                layout: {},
                energyAnswers: {},
                reportGenerated: false
            };
            
            // 步骤管理
            const steps = document.querySelectorAll('.step-content');
            const stepIndicators = document.querySelectorAll('.progress-step');
            let currentStep = 1;
            
            // 步骤切换函数
            function goToStep(stepNumber) {
                // 隐藏所有步骤
                steps.forEach(step => step.classList.remove('active'));
                // 显示目标步骤
                document.getElementById(`step${stepNumber}`).classList.add('active');
                
                // 更新进度指示器
                stepIndicators.forEach((indicator, index) => {
                    indicator.classList.remove('active', 'completed');
                    if (index + 1 < stepNumber) {
                        indicator.classList.add('completed');
                    } else if (index + 1 === stepNumber) {
                        indicator.classList.add('active');
                    }
                });
                
                currentStep = stepNumber;
            }
            
            // 初始化步骤1：出生年份选项
            function initBirthYearOptions() {
                const yearSelect = document.getElementById('birth-year');
                const currentYear = new Date().getFullYear();
                
                for (let year = currentYear; year >= currentYear - 80; year--) {
                    const option = document.createElement('option');
                    option.value = year;
                    option.textContent = year + '年';
                    yearSelect.appendChild(option);
                }
            }
            
            // 初始化步骤2：布局网格
            function initLayoutGrid() {
                const grid = document.getElementById('layout-grid');
                const directions = [
                    { dir: '北', pos: '正北位', key: 'north', row: 1, col: 2 },
                    { dir: '东北', pos: '东北位', key: 'northeast', row: 1, col: 3 },
                    { dir: '东', pos: '正东位', key: 'east', row: 2, col: 3 },
                    { dir: '东南', pos: '东南位', key: 'southeast', row: 3, col: 3 },
                    { dir: '南', pos: '正南位', key: 'south', row: 3, col: 2 },
                    { dir: '西南', pos: '西南位', key: 'southwest', row: 3, col: 1 },
                    { dir: '西', pos: '正西位', key: 'west', row: 2, col: 1 },
                    { dir: '西北', pos: '西北位', key: 'northwest', row: 1, col: 1 }
                ];
                
                // 中心单元格
                const centerCell = document.createElement('div');
                centerCell.className = 'grid-cell';
                centerCell.style.gridColumn = '2';
                centerCell.style.gridRow = '2';
                centerCell.innerHTML = `
                    <div class="direction-label">中心</div>
                    <div class="position-label">太极位</div>
                    <div class="item-icon"><i class="fas fa-home"></i></div>
                `;
                grid.appendChild(centerCell);
                
                // 八个方向单元格
                directions.forEach(dir => {
                    const cell = document.createElement('div');
                    cell.className = 'grid-cell';
                    cell.style.gridColumn = dir.col;
                    cell.style.gridRow = dir.row;
                    cell.dataset.direction = dir.key;
                    cell.innerHTML = `
                        <div class="direction-label">${dir.dir}</div>
                        <div class="position-label">${dir.pos}</div>
                        <div class="item-icon"><i class="fas fa-question"></i></div>
                    `;
                    
                    // 点击选择物品
                    cell.addEventListener('click', function() {
                        const selectedItem = document.querySelector('.item-option.selected');
                        if (selectedItem) {
                            const itemType = selectedItem.dataset.item;
                            const iconClass = selectedItem.querySelector('i').className;
                            
                            // 更新单元格显示
                            this.querySelector('.item-icon').innerHTML = `<i class="${iconClass}"></i>`;
                            this.dataset.item = itemType;
                            
                            // 存储到用户数据
                            userData.layout[dir.key] = itemType;
                        }
                    });
                    
                    grid.appendChild(cell);
                });
            }
            
            // 初始化步骤2：物品选择器
            function initItemSelector() {
                const itemSelector = document.getElementById('item-selector');
                const items = [
                    { icon: 'fas fa-couch', label: '沙发', value: 'sofa' },
                    { icon: 'fas fa-tv', label: '电视/柜', value: 'tv' },
                    { icon: 'fas fa-tree', label: '绿植', value: 'plant' },
                    { icon: 'fas fa-box', label: '储物柜', value: 'cabinet' },
                    { icon: 'fas fa-wind', label: '空调/风扇', value: 'ac' },
                    { icon: 'fas fa-lightbulb', label: '落地灯', value: 'lamp' },
                    { icon: 'fas fa-book', label: '书架', value: 'bookshelf' },
                    { icon: 'fas fa-question', label: '其他', value: 'other' }
                ];
                
                items.forEach(item => {
                    const option = document.createElement('div');
                    option.className = 'item-option';
                    option.dataset.item = item.value;
                    option.innerHTML = `
                        <i class="${item.icon}"></i>
                        <span>${item.label}</span>
                    `;
                    
                    option.addEventListener('click', function() {
                        // 移除其他选项的选择状态
                        document.querySelectorAll('.item-option').forEach(opt => {
                            opt.classList.remove('selected');
                        });
                        
                        // 标记当前选项为选中
                        this.classList.add('selected');
                    });
                    
                    itemSelector.appendChild(option);
                });
            }
            
            // 初始化步骤3：能量评估选项
            function initEnergyOptions() {
                const options = document.querySelectorAll('.option');
                options.forEach(option => {
                    option.addEventListener('click', function() {
                        const questionElement = this.closest('.energy-question');
                        const questionIndex = Array.from(document.querySelectorAll('.energy-question')).indexOf(questionElement);
                        
                        // 移除同一问题的其他选项的选择状态
                        questionElement.querySelectorAll('.option').forEach(opt => {
                            opt.classList.remove('selected');
                        });
                        
                        // 标记当前选项为选中
                        this.classList.add('selected');
                        
                        // 存储答案
                        userData.energyAnswers[`q${questionIndex + 1}`] = this.dataset.value;
                    });
                });
            }
            
            // 收集步骤1数据
            function collectStep1Data() {
                userData.name = document.getElementById('user-name').value || '未知用户';
                userData.birthYear = document.getElementById('birth-year').value;
                userData.careerType = document.getElementById('career-type').value;
                userData.financialIssue = document.getElementById('financial-issue').value;
                
                // 验证必填项
                if (!userData.birthYear || !userData.careerType || !userData.financialIssue) {
                    alert('请填写所有必填信息');
                    return false;
                }
                
                return true;
            }
            
            // 生成诊断报告
            function generateReport() {
                // 更新报告头部信息
                document.getElementById('report-user-name').textContent = userData.name;
                
                const careerTextMap = {
                    'metal': '金融/法律/管理（金）',
                    'wood': '教育/文化/创意（木）',
                    'water': '贸易/物流/咨询（水）',
                    'fire': '科技/能源/餐饮（火）',
                    'earth': '房地产/建筑/农业（土）'
                };
                document.getElementById('report-career-type').textContent = careerTextMap[userData.careerType] || userData.careerType;
                
                const now = new Date();
                document.getElementById('report-date').textContent = `${now.getFullYear()}年${now.getMonth() + 1}月${now.getDate()}日`;
                
                // 生成能量分数（基于算法）
                const scores = calculateEnergyScores();
                
                // 更新分数显示
                document.getElementById('score-opportunity').textContent = scores.opportunity;
                document.getElementById('score-risk').textContent = scores.risk;
                document.getElementById('score-stability').textContent = scores.stability;
                document.getElementById('score-help').textContent = scores.help;
                
                // 生成雷达图
                generateRadarChart(scores);
                
                // 生成问题诊断
                generateProblemDiagnosis(scores);
                
                // 生成解决方案
                generateSolutions();
                
                // 生成推荐产品
                generateRecommendedProducts();
                
                userData.reportGenerated = true;
            }
            
            // 计算能量分数
            function calculateEnergyScores() {
                // 基础分数（基于出生年份）
                let baseScore = 50;
                if (userData.birthYear) {
                    const year = parseInt(userData.birthYear);
                    const lastDigit = year % 10;
                    baseScore = 40 + lastDigit * 6;
                }
                
                // 职业类型加成
                const careerBonus = {
                    'metal': { opportunity: 15, risk: 10, stability: 20, help: 5 },
                    'wood': { opportunity: 20, risk: 5, stability: 10, help: 15 },
                    'water': { opportunity: 25, risk: 15, stability: 5, help: 10 },
                    'fire': { opportunity: 10, risk: 20, stability: 15, help: 5 },
                    'earth': { opportunity: 5, risk: 10, stability: 25, help: 10 }
                };
                
                const bonus = careerBonus[userData.careerType] || { opportunity: 0, risk: 0, stability: 0, help: 0 };
                
                // 布局影响
                let layoutBonus = { opportunity: 0, risk: 0, stability: 0, help: 0 };
                const southeastItems = Object.keys(userData.layout).filter(key => key === 'southeast' && userData.layout[key]);
                const northwestItems = Object.keys(userData.layout).filter(key => key === 'northwest' && userData.layout[key]);
                
                if (southeastItems.length > 0) layoutBonus.opportunity += 10;
                if (northwestItems.length > 0) layoutBonus.help += 10;
                
                // 答案影响
                let answerBonus = { opportunity: 0, risk: 0, stability: 0, help: 0 };
                const answers = userData.energyAnswers;
                
                if (answers.q1 === 'bright') answerBonus.stability += 10;
                if (answers.q1 === 'crowded') answerBonus.opportunity -= 5;
                if (answers.q2 === 'few' || answers.q2 === 'none') answerBonus.stability += 10;
                if (answers.q2 === 'many') answerBonus.risk -= 10;
                if (answers.q3 === 'lush') answerBonus.opportunity += 15;
                if (answers.q3 === 'none') answerBonus.opportunity -= 5;
                if (answers.q4 === 'opportunity') answerBonus.help += 5;
                if (answers.q4 === 'stagnation') answerBonus.opportunity += 10;
                
                // 计算最终分数
                const scores = {
                    opportunity: Math.min(100, Math.max(0, baseScore + bonus.opportunity + layoutBonus.opportunity + answerBonus.opportunity)),
                    risk: Math.min(100, Math.max(0, baseScore + bonus.risk + layoutBonus.risk + answerBonus.risk)),
                    stability: Math.min(100, Math.max(0, baseScore + bonus.stability + layoutBonus.stability + answerBonus.stability)),
                    help: Math.min(100, Math.max(0, baseScore + bonus.help + layoutBonus.help + answerBonus.help))
                };
                
                return scores;
            }
            
            // 生成雷达图
            function generateRadarChart(scores) {
                const radarChart = document.getElementById('radar-chart');
                radarChart.innerHTML = '';
                
                // 添加网格
                for (let i = 0; i < 3; i++) {
                    const grid = document.createElement('div');
                    grid.className = 'radar-grid';
                    radarChart.appendChild(grid);
                }
                
                // 分数点位置计算
                const centerX = 150;
                const centerY = 150;
                const radius = 100;
                
                const angles = [0, 90, 180, 270]; // 四个维度角度
                const labels = ['机遇敏感度', '贵人运势', '积累稳定性', '风险抵御力'];
                const scoreValues = [scores.opportunity, scores.help, scores.stability, scores.risk];
                
                // 添加标签
                labels.forEach((label, index) => {
                    const angle = angles[index] * Math.PI / 180;
                    const labelX = centerX + (radius + 30) * Math.sin(angle);
                    const labelY = centerY - (radius + 30) * Math.cos(angle);
                    
                    const labelElement = document.createElement('div');
                    labelElement.className = 'radar-label';
                    labelElement.textContent = label;
                    labelElement.style.left = `${labelX}px`;
                    labelElement.style.top = `${labelY}px`;
                    labelElement.style.transform = 'translate(-50%, -50%)';
                    radarChart.appendChild(labelElement);
                });
                
                // 添加分数点
                scoreValues.forEach((score, index) => {
                    const angle = angles[index] * Math.PI / 180;
                    const pointRadius = radius * (score / 100);
                    const pointX = centerX + pointRadius * Math.sin(angle);
                    const pointY = centerY - pointRadius * Math.cos(angle);
                    
                    const point = document.createElement('div');
                    point.className = 'radar-point';
                    point.style.left = `${pointX}px`;
                    point.style.top = `${pointY}px`;
                    radarChart.appendChild(point);
                });
            }
            
            // 生成问题诊断
            function generateProblemDiagnosis(scores) {
                const problemDiv = document.getElementById('problem-diagnosis');
                let diagnosisHTML = '';
                
                // 确定最低分维度
                let minScore = 100;
                let minDimension = '';
                
                for (const [dimension, score] of Object.entries(scores)) {
                    if (score < minScore) {
                        minScore = score;
                        minDimension = dimension;
                    }
                }
                
                // 基于最低分维度生成诊断
                const dimensionNames = {
                    opportunity: '机遇敏感度',
                    risk: '风险抵御力',
                    stability: '积累稳定性',
                    help: '贵人运势'
                };
                
                const dimensionIssues = {
                    opportunity: {
                        title: '机遇感知力待提升',
                        description: '您的家居能量场在东南方（巽位，象征流动财）可能存在阻塞，导致对新兴机会的敏感度不足，容易错过有价值的财务增长点。',
                        reason: '可能与东南方位物品摆放不当或能量流动不畅有关。'
                    },
                    risk: {
                        title: '财务风险抵御较弱',
                        description: '您的家居格局在正北方（坎位，象征风险抵御）能量不足，可能导致财务决策时缺乏足够的安全边界，易受意外支出或投资风险影响。',
                        reason: '正北方若有杂物堆积或阴暗潮湿，会削弱此方位能量。'
                    },
                    stability: {
                        title: '财富积累稳定性不足',
                        description: '西南方（坤位，关系财富积累）的能量场需要加强，这可能影响您的储蓄能力和长期财务稳定性，导致财富难以有效沉淀。',
                        reason: '西南方若有大型电器或流动性物品，会扰乱积累能量。'
                    },
                    help: {
                        title: '贵人助力通道不畅',
                        description: '西北方（乾位，象征贵人运）的能量流动可能受阻，这会影响您在事业和财务上获得关键帮助与资源支持的机会。',
                        reason: '西北方若有污秽物品或缺失重要能量元素，会关闭贵人通道。'
                    }
                };
                
                const issue = dimensionIssues[minDimension] || dimensionIssues.opportunity;
                
                diagnosisHTML = `
                    <div style="margin-bottom: 25px;">
                        <h4 style="color: var(--accent-gold); margin-bottom: 10px;">${issue.title}</h4>
                        <p>${issue.description}</p>
                        <p>${issue.reason}</p>
                    </div>
                    <div style="background-color: rgba(212, 175, 55, 0.05); padding: 20px; border-radius: 8px; border-left: 3px solid var(--accent-gold);">
                        <h4 style="color: var(--accent-light); margin-bottom: 10px;">💡 专业解读</h4>
                        <p>在传统风水学中，家居的八个方位对应不同的生命领域。${userData.name}的家居能量评估显示，您的${dimensionNames[minDimension]}得分仅为${minScore}分，是四个维度中最需要优化的领域。结合您的${careerTextMap[userData.careerType] || ''}职业属性，这可能会放大您在财务上的特定挑战。</p>
                    </div>
                `;
                
                problemDiv.innerHTML = diagnosisHTML;
            }
            
            // 生成解决方案
            function generateSolutions() {
                // 移动方案
                const moveSolutions = {
                    metal: '建议移走客厅正西（兑位）和西北（乾位）的红色物品或尖锐金属物品，这些会与您的"金"属性产生冲突，消耗财运能量。',
                    wood: '建议清理东南（巽位）堆积的金属物品或废旧电器，这些会压制您的"木"属性生长能量，阻碍新的财务机会。',
                    water: '建议移走客厅正南（离位）的大型土质装饰或陶瓷摆件，这些会形成"土克水"格局，阻碍财富流动。',
                    fire: '建议移走正北（坎位）的大型水元素装饰或黑色家具，这些会与您的"火"属性形成"水克火"格局，压制财运能量。',
                    earth: '建议清理正东（震位）和东南（巽位）的过多绿植或木质家具，这些会形成"木克土"格局，消耗您的稳定积累能量。'
                };
                
                document.getElementById('solution-move').innerHTML = 
                    moveSolutions[userData.careerType] || '建议定期清理家中各角落的杂物，特别是西南（坤位）和东北（艮位），保持能量流动通畅。';
                
                // 增加方案
                const addSolutions = {
                    metal: '在客厅西北（乾位）增加白色、金色或圆形金属饰品，如铜铃、金属摆件，强化贵人运势与决策力。',
                    wood: '在客厅东南（巽位）增加健康绿植或木质装饰，如发财树、绿萝，并用小型流水装饰激活财运流动。',
                    water: '在客厅正北（坎位）增加蓝色、黑色装饰或小型水景，如鱼缸、流水摆件，增强财富流动性与风险抵御力。',
                    fire: '在客厅正南（离位）增加红色、紫色装饰或温和光源，如红色靠垫、盐灯，激活财运能量与行动力。',
                    earth: '在客厅西南（坤位）增加黄色、棕色陶器或水晶洞，如黄水晶、陶瓷花瓶，强化财富积累稳定性。'
                };
                
                document.getElementById('solution-add').innerHTML = 
                    addSolutions[userData.careerType] || '在客厅财位（根据具体户型确定）增加与您五行相生的能量物品，增强整体财运能量场。';
                
                // 强化方案
                const strengthenSolutions = {
                    metal: '在书房或工作区摆放白水晶簇或铜制文昌塔，强化决策智慧与职业发展，帮助抓住关键财务机会。',
                    wood: '在阳台或窗台摆放开运竹或兰花，配合绿色窗帘，建立"生机勃勃"的能量场，吸引成长性财富机会。',
                    water: '在进门对角线位置（明财位）摆放黑曜石或海蓝宝水晶，配合小型流水装置，建立"财源滚滚"的能量循环。',
                    fire: '在客厅中心区域摆放紫水晶或红色玛瑙摆件，配合暖色调灯光，激活"热情积极"的财运能量场。',
                    earth: '在卧室西南角摆放黄水晶或陶瓷聚宝盆，配合稳定光源，建立"厚实稳固"的财富积累能量场。'
                };
                
                document.getElementById('solution-strengthen').innerHTML = 
                    strengthenSolutions[userData.careerType] || '在家中财位摆放与您命理五行相匹配的水晶或能量摆件，持续强化财运能量场。';
            }
            
            // 生成推荐产品
            function generateRecommendedProducts() {
                const productsDiv = document.getElementById('recommended-products');
                
                const productsByCareer = {
                    metal: [
                        { name: '黄铜招财麒麟', price: '¥368', icon: 'fas fa-dragon' },
                        { name: '白水晶能量簇', price: '¥458', icon: 'fas fa-gem' },
                        { name: '五行金属风铃', price: '¥298', icon: 'fas fa-wind' }
                    ],
                    wood: [
                        { name: '天然紫檀木财神', price: '¥588', icon: 'fas fa-tree' },
                        { name: '绿幽灵水晶摆件', price: '¥428', icon: 'fas fa-leaf' },
                        { name: '文昌塔绿植套装', price: '¥328', icon: 'fas fa-seedling' }
                    ],
                    water: [
                        { name: '黑曜石七星阵', price: '¥518', icon: 'fas fa-circle' },
                        { name: '流水生财摆件', price: '¥398', icon: 'fas fa-water' },
                        { name: '海蓝宝原石', price: '¥368', icon: 'fas fa-gem' }
                    ],
                    fire: [
                        { name: '紫水晶洞聚宝盆', price: '¥688', icon: 'fas fa-mountain' },
                        { name: '红玛瑙能量柱', price: '¥358', icon: 'fas fa-fire' },
                        { name: '太阳石摆件', price: '¥428', icon: 'fas fa-sun' }
                    ],
                    earth: [
                        { name: '黄水晶聚宝树', price: '¥558', icon: 'fas fa-tree' },
                        { name: '陶瓷貔貅摆件', price: '¥488', icon: 'fas fa-paw' },
                        { name: '泰山石敢当', price: '¥398', icon: 'fas fa-mountain' }
                    ]
                };
                
                const products = productsByCareer[userData.careerType] || productsByCareer.metal;
                
                productsDiv.innerHTML = '';
                products.forEach(product => {
                    const productCard = document.createElement('div');
                    productCard.className = 'product-card';
                    productCard.innerHTML = `
                        <div class="product-img">
                            <i class="${product.icon}"></i>
                        </div>
                        <div class="product-info">
                            <div class="product-name">${product.name}</div>
                            <div class="product-price">${product.price}</div>
                            <a href="#" class="btn-buy">立即请购</a>
                        </div>
                    `;
                    
                    // 购买按钮事件
                    productCard.querySelector('.btn-buy').addEventListener('click', function(e) {
                        e.preventDefault();
                        alert(`感谢您对${product.name}的兴趣！请添加客服微信：caistart888 了解更多详情。`);
                    });
                    
                    productsDiv.appendChild(productCard);
                });
            }
            
            // 事件监听器
            document.getElementById('next-to-step2').addEventListener('click', function() {
                if (collectStep1Data()) {
                    goToStep(2);
                }
            });
            
            document.getElementById('back-to-step1').addEventListener('click', function() {
                goToStep(1);
            });
            
            document.getElementById('next-to-step3').addEventListener('click', function() {
                // 检查是否至少选择了一个布局物品
                const selectedItems = Object.keys(userData.layout).length;
                if (selectedItems === 0) {
                    alert('请至少选择一个物品并点击布局图中的方位进行摆放');
                    return;
                }
                
                goToStep(3);
            });
            
            document.getElementById('back-to-step2').addEventListener('click', function() {
                goToStep(2);
            });
            
            document.getElementById('generate-report').addEventListener('click', function() {
                // 检查是否回答了所有能量问题
                const answeredQuestions = Object.keys(userData.energyAnswers).length;
                if (answeredQuestions < 4) {
                    alert('请完成所有能量评估问题');
                    return;
                }
                
                generateReport();
                goToStep(4);
            });
            
            document.getElementById('back-to-step3').addEventListener('click', function() {
                goToStep(1);
            });
            
            document.getElementById('save-report').addEventListener('click', function() {
                alert('报告已保存！您也可以截图保存此页面。如需专业咨询，请添加客服微信：caistart888');
            });
            
            document.getElementById('copy-link').addEventListener('click', function() {
                navigator.clipboard.writeText(window.location.href)
                    .then(() => alert('报告链接已复制到剪贴板！'))
                    .catch(() => alert('复制失败，请手动复制网址'));
            });
            
            // 分享按钮事件
            document.querySelector('.share-wechat').addEventListener('click', function() {
                alert('请使用微信扫描分享二维码\n\n专业财运诊断，快来测测你的家居能量场！');
            });
            
            document.querySelector('.share-redbook').addEventListener('click', function() {
                alert('请打开小红书App分享此页面\n\n#财运测试 #家居风水 #能量提升');
            });
            
            // 初始化所有组件
            initBirthYearOptions();
            initLayoutGrid();
            initItemSelector();
            initEnergyOptions();
        });
    </script>
</body>
</html>
